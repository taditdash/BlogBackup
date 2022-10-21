# Vuetify Rounded Card Design

The idea is to customize the corners of the `v-card` component in Vuetify so that it looks rounded. Let's see what is the impediment and how to overcome that easily.

## Background

While working on designing a Billing Subscription Box in a current project, the requirement was to design rounded corners instead of normal corners.

## Let's Code

Let's first have a normal card that would look something like below.

![Normal-Card.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1631807663389/WATlYYDYc5.png)

The code is pretty simple, isn't it!

```
<v-card>
  <v-card-title>Tadit Dash</v-card-title>
  <v-card-subtitle>Tadit Dash is an Indian by heart, a Software Engineer by profession, an Author and a Speaker by passion.</v-card-subtitle>
  <v-card-actions>
	<v-btn icon>
	  <v-icon>mdi-web</v-icon>
	</v-btn>
	<v-btn icon>
	  <v-icon>mdi-twitter</v-icon>
	</v-btn>
	<v-btn icon>
	  <v-icon>mdi-linkedin</v-icon>
	</v-btn>
	<v-btn icon>
	  <v-icon>mdi-facebook</v-icon>
	</v-btn>
	<v-btn icon>
	  <v-icon>mdi-instagram</v-icon>
	</v-btn>
  </v-card-actions>
</v-card>
```

Now let's go to Vuetify Documentation and find out if there is any way to make the corners round. Here it is - [https://vuetifyjs.com/en/components/cards/](https://vuetifyjs.com/en/components/cards/)

![v-card-Shaped-Property.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1631807709219/NLjF0ZIoA.png)

I can see that there is a property named `shaped`, which helps to add `border-radius`. That is what we needed. Let's try that and see what happens.

![Shaped-Card.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1631807816006/mpFujYkPL.png)

Wow! We can see the corners are rounded now. However, only the left top and bottom right are having rounded corners. If this is what you need, then your work is done. Copy the code below and enjoy.
```
<v-card shaped>
  <v-card-title>Tadit Dash</v-card-title>
  <v-card-subtitle>
	<!--Removed for brevity-->
  </v-card-subtitle>
  <v-card-actions>
	<!--Removed for brevity-->
  </v-card-actions>
</v-card>
```

But I need something else. I wanted all the corners to be rounded which is not possible by default. Then the option here is to do it myself. For that, let's analyze the rendered HTML first.

![v-card-Shaped-Rendered-HTML-1-1024x324.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1631815506285/9COC8j3z5.png)

So, it's quite clear how the corners are getting added under the hood. The following CSS is helping to add a radius at every corner.

```
.v-card--shaped {
  border-radius: 24px 4px;
}
```

But it is not uniform. Top Left, Bottom Right is `24px` and Top Right, Bottom Left is `4px`. To make it the same across all the corners we need to add the same radius, of course. To do that, we can add a class to the `v-card` and write CSS rules accordingly.

```
<v-card shaped class="rounded-card mx-auto mt-5" max-width="344">
  <!--Removed for brevity-->
</v-card>

<style type="text/css">
  .rounded-card {
      border-radius: 24px;
  }
</style>
```

After this change, the rendered HTML is modified with a radius to all the corners. Screenshot below.

![v-card-Shaped-Rendered-HTML-with-all-Rounded-Corners-1-1024x321.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1631815398369/wJ8lsWCow.png)

The class `rounded-card` takes over the `border-radius` property and `v-card--shaped` is no more applied. The card looks rounded now as all the corners are having a uniform radius. You can increase the radius as per your needs.

## Here is the CodePen

%[https://codepen.io/taditdash/pen/YzyWQJb]

## Help Someone

Share in your circle. Hit the social icons to share. Keep coding folks. 🙂

Thanks for reading, have a great day ahead.

## It takes 7 Days to learn Vue.js

Yes, you heard that right. I have co-authored a book that comprehensively takes you in a 7 days journey to learn the basics of Vue.js. You can buy that from [Amazon.com](https://www.amazon.com/gp/product/9388511867/ref=dbs_a_def_rwt_bibl_vppi_i1) or [Amazon.in](https://www.amazon.in/Learn-Vue-js-Days-Journey-through/dp/9388511867/ref=tmm_pap_swatch_0?_encoding=UTF8&qid=&sr=) or [BPB Official Website](https://bpbonline.com/products/learn-vue-js-in-7-days).  
More at - [https://taditdash.co.in/#Vuejs7Days](https://taditdash.co.in/#Vuejs7Days)