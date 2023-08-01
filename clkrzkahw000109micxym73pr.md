---
title: "Get Required Property from Complex json string in C# with Newtonsoft"
datePublished: Fri Dec 25 2015 11:52:40 GMT+0000 (Coordinated Universal Time)
cuid: clkrzkahw000109micxym73pr
slug: get-required-property-from-complex-json-string-in-c-with-newtonsoft
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1686903830622/e28a3616-e942-4251-95d9-eb430f3c81d8.png
tags: json, net, nuget, newtonsoft

---

## Introduction

In this blog, I will explain the trick to convert JSON string property to C# Object using Newtonsoft.

## Illustration

Suppose the JSON string is like…

```json
{
  "Success": true,
  "ComplexObject": {
    "NormalProp": "Test",
    "ListOfAnotherClass": [{
      "JustAStringProp": "We"
    }, {
      "JustAStringProp": "Got"
    }, {
      "JustAStringProp": "Values"
    }]
  }
}
```

Now, if I get this `string` from some method and try to process, I would need to convert this to C# objects. The structure would look something like below. To easily get the class structure, you can use any online tool like [json2csharp](http://json2csharp.com/).

```csharp
class Result
{
    public bool Success { get; set; }
    public ComplextJsonClass ComplexObject { get; set; }
}
 
class ComplextJsonClass
{
    public string NormalProp { get; set; }
    public List<AnotherClass> ListOfAnotherClass { get; set; }
}
 
class AnotherClass
{
    public string JustAStringProp { get; set; }
}
```

## What We Need?

So, for processing, I would like to get the “`ComplexObject`” property of this JSON `string` converted as “`ComplextJsonClass`” C# object. As the JSON `string` is complex with other properties like “`Success`“, we only need the property “`ComplexObject`“, yet converted to a C# object.

## How To Do That?

We will use [Newtonsoft](https://www.nuget.org/packages/newtonsoft.json/). You can easily find that from **Nuget** and add that as a reference to your project.

## Solution

First, I will tell you how to generate this type of JSON.

```csharp
var complex = new ComplextJsonClass
{
    NormalProp = "Test",
    ListOfAnotherClass = new List<AnotherClass>
    {
        new AnotherClass{JustAStringProp = "We"},
        new AnotherClass{JustAStringProp = "Got"},
        new AnotherClass{JustAStringProp = "Values"},
    }
};
 
var moreComplex = new Result {Success = true, ComplexObject = complex};
var jsonString = JsonConvert.SerializeObject(moreComplex);
```

This “`jsonString`” comes as I mentioned at the beginning of the post. Now, we need to convert this JSON to a C# Object. For this, we need to use [JsonConvert.DeserializeObject Method (String)](http://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject.htm).

```csharp
	var jsonObject = JsonConvert.DeserializeObject(jsonString);
```

But, unfortunately, this alone won’t help us more to access the properties. We have to convert to a [**JObject**](http://www.newtonsoft.com/json/help/html/t_newtonsoft_json_linq_jobject.htm), by which we can easily access the properties from the JSON.

```csharp
var jsonObject = (JObject)JsonConvert.DeserializeObject(jsonString);
```

After this, it is just a matter of getting the property by using `jsonObject["ComplexObject"]`.

```csharp
var jsonObject = (JObject)JsonConvert.DeserializeObject(jsonString);
if (jsonObject["ComplexObject"] == null) return;
 
ComplextJsonClass complexObject = JsonConvert.DeserializeObject<ComplextJsonClass>
            (jsonObject["ComplexObject"].ToString());
```

![Convert to C# Object from Newtonsoft JObject](https://cdn.hashnode.com/res/hashnode/image/upload/v1686903827462/ecfc55d8-02f3-4774-8027-5c45a33f8873.png align="left")

## Full Code

```csharp
var complex = new ComplextJsonClass
{
    NormalProp = "Test",
    ListOfAnotherClass = new List<AnotherClass>
    {
        new AnotherClass{JustAStringProp = "We"},
        new AnotherClass{JustAStringProp = "Got"},
        new AnotherClass{JustAStringProp = "Values"},
    }
};
 
// Get the jsonString from complex object.
var moreComplex = new Result {Success = true, ComplexObject = complex};
var jsonString = JsonConvert.SerializeObject(moreComplex);
 
//Now let's deserialize and convert to our required ComplextJsonClass object.
var jsonObject = (JObject)JsonConvert.DeserializeObject(jsonString);
if (jsonObject["ComplexObject"] == null) return;
 
ComplextJsonClass complexObject = JsonConvert.DeserializeObject<ComplextJsonClass>
            (jsonObject["ComplexObject"].ToString());
```

## Feedback

Let me know if this trick helped you in any way in your projects or assignments. Re-post or share, if you liked it.

Thanks a lot for reading. Merry Christmas and Happy New Year. 😀🤝