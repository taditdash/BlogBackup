## Configure Vee Validate for Localisation using Vue I18N Library

# Introduction
In this blog, we will learn how to configure `vee-validate` library so that it would work for translations with the internationalization library `vue-i18n`.

# Background
I am working on a project that is built with Vue.js and set up for internationalization with `vue-i18n` library. The validations are done with the help of [vee-validate](https://vee-validate.logaretm.com/v4/) library that provides out-of-the-box validations for different types of validations like required fields, minimum length, maximum length, etc.

The project is working perfectly. It has a certain code to read the translations from the JSON files inside the *src/locales* directory.

I did follow this [article](https://lokalise.com/blog/vue-i18n/) from lokalise to set up everything.

# Assumptions
I will make some assumptions as this is not a beginner write-up. Here is the list of assumptions on a project that you might have already built.
1. Vue.js is setup and running
2. Vee-Validate library is integrated for validations
3. Vue-I18N library is set up for translations
4. JSON files for translations are available inside the directory **src/locales** with key and value structure

# Problem
Now the challenge is to include the `vee-validate` validation message translations to work seamlessly with `vue-i18n` library.
When I say validation messages then it contains two things.
1. The field name that we are validating
2. The validation message according to the validation type

Let's go through the following examples to understand the above points.

Let's say we have a **First Name** field that is required. So, the validation message that would show when you don't enter anything would be something like the below.

![The First Name field is required.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1631592279306/Ph4yeusFE.png)

Here, if we want to translate the validation messages, then we have to translate the field (`First Name`) and then the validation message (`The {field} field is required`). Essentially the field is a variable here.

Now you must be thinking why can't we just have the translations for the whole string, that is because there might be a lot of fields in your whole project. Moreover, the validations messages are not just for required fields. These messages can be a lot complicated. 

Just Imagine a `password` field with the following setup for validations.
1. It is required
2. It can contain different types of characters
3. It should be more than 8 chars and less than 13 characters

In this case, there will be different messages and it is totally not scalable to have translations of the whole messages. That's why the field names should be translated and stored in JSON files that we already have. However, no need to translate the validation messages except the field name because the library is already having them for all language types.

For `vee-validate`, we can see the translated validation messages inside the *node-modules/vee-validate/dist/locales*.

# Solution
Let's discuss how to solve this problem. When you work with `vue-i18n` library, there will be some code that would be auto-generated when you install the package using the `vue-cli` command `vue add i18n`. You can follow the lokalise [article](https://lokalise.com/blog/vue-i18n/) for details. I will focus on our specific problem. So, one of that scaffolded files is *src/i18n.js*. Let's have a sneak peek.

```
// src/i18n.js

import Vue from 'vue'
import VueI18n from 'vue-i18n'

Vue.use(VueI18n)

function loadLocaleMessages () {
  const locales = require.context('./locales', true, /[A-Za-z0-9-_,\s]+\.json$/i)
  const messages = {}
  locales.keys().forEach(key => {
    const matched = key.match(/([A-Za-z0-9-_]+)\./i)
    if (matched && matched.length > 1) {
      const locale = matched[1]
      messages[locale] = locales(key)
    }
  })
  return messages
}

export default new VueI18n({
  locale: process.env.VUE_APP_I18N_LOCALE || 'en',
  fallbackLocale: process.env.VUE_APP_I18N_FALLBACK_LOCALE || 'en',
  messages: loadLocaleMessages()
})
``` 
Essentially we are trying to import `Vue` and `VueI18n` libraries so that we can configure the translations.

Notice the function `loadLocaleMessages` which is helping us to load all messages from the JSON translation files that reside inside the *src/locales* directory. The code `messages[locale] = locales(key)` is pulling all our translations from a specific file represented by the key, for example, "./de.json" for German. Then it stores in a property represented by the locale param. Thus, it becomes the object shown below in the screenshot.

![Translation Messages Object View.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1631593154408/kNBfhGxWq.png)

And it continues to add properties with the locale names to this object as it loops through all locales.

At last, a VueI18n is exported containing the locale from the `.env` file or default one as `'en'`, also a `fallbackLocale` and the `messages` that we just retrieved from the JSON files.

Now the interesting part. We need to integrate the `vee-validate` messages. Let's see the problem in the first place with the screenshot below.

![The First Name field is required 2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1631592368236/kSdKOg9Vb.png)

As you can see here, the First Name label is now changed to **Nombre** for the Spanish language (Imagine I have a language switcher with different languages), however, the validation message is still in English. That is what we need to fix. Let's find a way.

We already discussed a simple logic of splitting the validation message into two parts. `The First Name field is required` follows a patern `The {_field_} field is required` where `{_field_}` is **First Name**.

Now somehow we need to code for two things.
1. Ask `VueI18n` to include all the validation messages for all languages 
2. Replace `{_field_}` with the field name translation from our translation files

## Ask `VueI18n` to include all the validation messages for all languages

It is a bit tricky till I figured out the solution. It's totally my hack. Let's see how we can do. Obviously, we have to do something where all the translations are fetched. Do you remember where?

Yes, it's our well-known `loadLocaleMessages()`. Let's make some modifications.

```
// src/i18n.js

function loadLocaleMessages () {
  const locales = require.context('./locales', true, /[A-Za-z0-9-_,\s]+\.json$/i)
  const messages = {}

  locales.keys().forEach(key => {
    const matched = key.match(/([A-Za-z0-9-_]+)\./i)
    if (matched && matched.length > 1) {
      const locale = matched[1]
      messages[locale] = locales(key)

      // Load the validation messages from vee-validate 
      // library into the messages object.
      messages[locale].validation = getVeeValidateLocale(locale).messages
    }
  })
  return messages
}

function getVeeValidateLocale (locale) {
  // Get validation messages from vee-validate locale file.
  // If locale 'en', then get the messages from "vee-validate/dist/locale/en.json"
  // If locale 'es', then get the messages from "vee-validate/dist/locale/de.json"
}

```
Notice that we have a new code inside the `forEach` that will fetch the validation messages according to the locale that we are looping and then place it as a validation property of the messages locale object. We will see it in a while. Just stay with me a little bit.

That means here we need to somehow ask `vee-validate` library to give us the translated validation messages. To do that, we have to do the following.
1. Import the validation JSON files containing the translated messages
2. Get the validation messages for the particular locale that is passed to the `getVeeValidateLocale()`. 

Let's complete these one by one. 
### Import the validation JSON files containing the translated messages
For importing, we can write the import statements like the following.

```
// src/i18n.js

import en from "vee-validate/dist/locale/en.json" // English validation messages.
import de from "vee-validate/dist/locale/de.json" // German validation messages. 
import es from "vee-validate/dist/locale/es.json" // Spanish validation messages.

// ... Import statements for other languages
```

Don't trust me on here about the translated validation messages! Let me give you a quick look at one of these files. Here is the *es.json* file that is available from `vee-validate`.

```
// node_modules/vee-validate/dist/locale/es.json

{
  "code": "es",
  "messages": {
    // ... removed for brevity

    "email": "El campo {_field_} debe ser un correo electrónico válido",
    
    "max": "El campo {_field_} no debe ser mayor a {length} caracteres",
    "max_value": "El campo {_field_} debe de ser {max} o menor",
    
     // ... removed for brevity

    "numeric": "El campo {_field_} debe contener solo caracteres numéricos",
    "regex": "El formato del campo {_field_} no es válido",
    "required": "El campo {_field_} es obligatorio",
    "required_if": "El campo {_field_} es obligatorio",
    "size": "El campo {_field_} debe ser menor a {size}KB"
  }
}

```
This JSON file is basically a collection of validation messages according to the type of validation.

In here, see the item `"required": "El campo {_field_} es obligatorio"` which is actually the translated message for the required field type validation message, for instance `The {_field_} field is required` in English. Here `{_field_}` is the variable where we will place the translation for the field. We will do that in the next section.

### Get the validation messages for the particular locale that is passed to the `getVeeValidateLocale(locale)`

Now that we know where to get the messages from, let's populate some code inside the function `getVeeValidateLocale(locale)`.

```
// src/i18n.js

// ... other codes...

function getVeeValidateLocale (locale) {
  if (locale == 'en') {
    return en;
  } else if (locale == 'de') {
    return en;
  } else if (locale == 'es') {
    return es;
  }
  // ...

  return en;
}

```
Basically, we are trying to say to return the appropriate imported locale JSON file according to the locale passed as an argument, else default as *English (en)*. However, clearly, this is not a good approach because `if else` can make this code unnecessarily long. We can definitely do better than this.

Can we do a `switch case`? Again, the same kind of code isn't it. We have one more nice option. **Object Literals**. This would definitely minimize the amount of code for this requirement. Let's see.

```
function getVeeValidateLocale (locale) {
  const veeValidateLocales = {
    'en': en, 
    'de': de,
    'es': es,
    //...
    'default': en
  };

  return veeValidateLocales[locale] || veeValidateLocales['default'];
}

```
Simple and clean. An object a declared with a collection of **name-value** pairs. To select a particular item we can select it using the syntax `object_name['property name']`. You can read more about this at [Working with objects](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects).

This can be optimized more as the name and value are the same except the default one.

```
// You can add more languages to this object as needed.
function getVeeValidateLocale (locale) {
  const veeValidateLocales = { en, de, es, 'default': en };

  return veeValidateLocales[locale] || veeValidateLocales['default'];
}
```

Let's put a debugger now to see how this works at `messages[locale].validation = getVeeValidateLocale(locale).messages`. Here is the browser console screenshot.

![Validation Translations.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1631592538796/BBmYeBxpG.png)

Beautiful, now we are able to get the translated validation messages. The only thing left here is to replace the `{_field_}` with the actual translated field name.

## Replace `{_field_}` with the field name translation from our translation files

This is easy as we already have the translations for the field names in our JSON files as we see **Nombre** for the First Name field for Spanish. So, we need to just load the same translation for the validation message.

Your translation JSON file for Spanish might look something like this.

```
// src/locales/es.json

{
    "fieldFirstName": "Nombre"
    // ... other translation keys and values.
}
```
That means we just need to find the value of this `key` for the First Name field as an example. Assuming that you have a running setup of `vee-validate` with the Vue project, here is the code to update the default messages that can run for every field when validation comes into picture.

```
// src/main.js

// ... other codes

import { configure } from 'vee-validate'
import * as rules from 'vee-validate/dist/rules'
import i18n from './i18n'

configure({
  defaultMessage: (field, values) => {
    // Remove whitespace inside the field name
    let fieldName = field.replace(/\s+/g, "");

    values._field_ = i18n.t(`field${fieldName}`);

    return i18n.t(`validation.${values._rule_}`, values);
  }
});

// ... other codes
```
This `defaultMessage` function runs for all fields that become active on the page. Assuming that it is currently running for the field "First Name", let's try to understand line by line.
1. The argument `field` possesses **First Name** (comes from the input tag configuration)
2. `let fieldName = field.replace(/\s+/g, "");`: This would remove all whitespace inside the field name, so now `fieldName` is **FirstName**
3. The param `values` contains the details about the particular validation, see the console output below.
![The values param inside the vee-validate defaultMessage function.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1631594294669/szknW-hWg.png)
4. So, now, we need to translate the `values._field_` property that we are doing next with the code
```values._field_ = i18n.t(`field${fieldName}`);```
The `i18n.t()` function is used to get the translation for a key, here the key is `fieldFirstName`. Remember the JSON file I showed above contained this key and its translation for the Spanish language.
5. Now that we are done with the field name translation, we can now replace the this in the whole validation message that we stored in messages locale's validation property. That is done by ```i18n.t(`validation.${values._rule_}`, values)```. Here the `values` is a param that is passed to this `i18n.t()` is responsible for the replacement of `{_field_}` which is available in the `validation.required` as `_rule_` is **required**.

With this, our code is configured to work. Here is how it would look like.

![Translated validation message.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1631596018264/WfZEpSarQ.png)

There is just one last thing you have to do if you have a mechanism to switch the language. You just need to trigger a refresh for the messages as soon as you switch the language, which can be done by calling the `localeChanged()` from `vee-validate` library. If you don't do this, the validation message will still be translated but would be lazy and won't show up till you make a mistake.

Here is the example code to fire an immediate change of language when you switch languages.

```
import { localeChanged } from 'vee-validate';

// ... other codes

switchLocale() {
  if (this.$i18n.locale !== this.selectedLocale.val) {
    this.$i18n.locale = this.selectedLocale.val;
    localeChanged();
  }
}

// ... other codes
```

# Feedback
I hope this blog helps someone in resolving the case of integrating `vee-validate` with `vue-i18n`.

In case you face some issues or have some feedback, feel free to add a comment below and I will definitely reply once I see it.

If you find this useful, please share it on your social channels.

Thanks for reading. Have a nice day ahead. 😎