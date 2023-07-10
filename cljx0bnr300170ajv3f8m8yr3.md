---
title: "EntityType: EntitySet ‘[Entity Name]’ is based on type ‘[Entity Name]’ that has no keys defined"
datePublished: Mon Nov 09 2015 12:28:38 GMT+0000 (Coordinated Universal Time)
cuid: cljx0bnr300170ajv3f8m8yr3
slug: entitytype-entityset-entity-name-is-based-on-type-entity-name-that-has-no-keys-defined
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/npxXWgQ33ZQ/upload/dd6380247a6491b4b69118a87b2885de.jpeg
tags: entity-framework, mvc, aspnet-mvc, primary-key, systemdataentityedmedmentityset

---

So, the exception completely indicates to us that it is not able to find a Key in the model, which is defined in the database for that entity.

## Problem

When you design a model class for the entity, you define many properties including keys, if any. But how MVC would know that some property is a key and some other is a normal? There should be some rule, right? Yes, there is. And if you don’t follow that rule, you would definitely get the below exception.

> EntityType: EntitySet '*\[Entity Name\]*' is based on type '*\[Entity Name\]*' that has no keys defined.

## Solution

MVC will automatically recognize an entity’s Key if it follows the convention ‘Id’ or ‘EntityNameId’. Additionally, the entity must expose this as a **PROPERTY** AND it must be **PUBLIC**. If you don’t follow the convention, then you need to explicitly indicate that particular property as a Key by using an annotation.

Let’s explore more below.

## Example

### Convention ‘Id’ or ‘EntityNameId’

```csharp
public int Id { get; set; }
```

OR

```csharp
public int EntityNameId { get; set; }
```

### Using \[Key\] Attribute

Just put `[Key]` on top of your property (which is presenting primary key). Something like this.

```csharp
[Key]
public int AnyName { get; set; }
```

## Hope this Helps !!!

If you landed on this page by searching for the issue somewhere, then I would like you to comment here if you have more queries or doubts. Thanks for reading the blog.

Share if you care. 👌