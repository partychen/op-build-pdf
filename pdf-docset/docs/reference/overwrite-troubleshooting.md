# Troubleshooting overwrites

If you feel like you're stuck in a trial-and-error mode, throwing @#$%^ at the wall and it's not sticking, check out some of the solutions to common problems below. 

This article is intended to help with overwrite-specific issues, not necessarily common Markdown issues. For Markdown help, see the [Markdown section in the Docs Contributor Guide](https://stage.docs.microsoft.com/en-us/contribute/markdown), or the [OPS User Guide](https://opsdocs.azurewebsites.net/en-us/opsdocs/partnerdocs/gfm?branch=master).

> [!TIP]
> The DocFx [overwrite files documentation](https://dotnet.github.io/docfx/tutorial/intro_overwrite_files.html) page has a good overview of how overwrites work, and what exactly can be overwritten.
>

### Issue: I can't get *anything* to show for my overwrite. In fact, none of my overwrites seem to work for a given .md file, or they just stop at a certain point.

**Extraneous (`:`) colon character**  
A common cause of this is due to a colon being used in the overwrite text. This is because the overwrite file syntax uses the YAML format to express the name/value pairs, and YAML specifies a single colon per line to separate the overwrite name/value pair.

For example, if you have a overwrite that looks like the following, the extraneous `:` in the description for the `api-version` parameter overwrite will cause an exception in the build and none of your overwrites will be applied to the final page/output.

```
---
uid: management.azure.com/RateCardManagementClient/2015-06-01-preview/RateCard_Get
parameters:
    - name: api-version
      description: Use the latest version: `2016-08-31-preview`.
    - name: subscriptionId
      description: The identifier of the target Azure subscription. 
description: *content
---
```

**Extraneous `---` separator** in a overwrite  
As with other issues, this is about making sure you have valid YAML. If your description overwrite contains extra `---` delimiter at the end for example (like the one below), this will also cause an exception in the build and none of your overwrite will be applied to the final page/output.

```
---
uid: management.azure.com/RateCardManagementClient/2015-06-01-preview/RateCard_Get
description: *content
---
<content>
---
<EOF > 
```

### Issue: My exception overwrite is not working.
For example, the following will not overwrite the text for the specified exception:

```
---
uid: Microsoft.ServiceBus.Messaging.TopicDescription.EnableFilteringMessagesBeforePublishing
exceptions: *content
---
[NoMatchingSubscriptionException](/dotnet/api/microsoft.servicebus.messaging.nomatchingsubscriptionexception)

Thrown if no subscriptions are found.
```

Instead, you need to use one the following formats:

```
---

uid: Microsoft.ServiceBus.Messaging.TopicDescription.EnableFilteringMessagesBeforePublishing
exceptions: 
- type: Microsoft.ServiceBus.Messaging.NoMatchingSubscriptionException 
  description: Thrown if no subscriptions are found.
---
```
 
Or:

```
---

uid: Microsoft.ServiceBus.Messaging.TopicDescription.EnableFilteringMessagesBeforePublishing
exceptions: 
- type: Microsoft.ServiceBus.Messaging.NoMatchingSubscriptionException
  description: *content
---
Thrown if no subscriptions are found.

```
### Issue: My list is not rendering correctly.

> [!NOTE]
> This issue was originally caused by [801775](https://mseng.visualstudio.com/DefaultCollection/VSChina/_workitems?_a=edit&id=801775). However, as of 12/15/16, this has been resolved. Please reopen the bug above if you find differently, or find other/related issues with list items.
>

For example, sometimes when you do an overwrite of an item (say, a description), you need to use the "*content" keyword to do more than just overwrite a few words or single line. Sometimes you want to do a whole block of Markdown text, with an unordered list, like this: 

```
description: *content
---

## Test
- bullet 1  
- bullet 2  
- bullet 3  

```

But when the Markdown renders, it ends up looking something like this, where your bullets are misaligned with the text above them:

<b>Test</b>
<li>bullet 1</li>
<li>bullet 2</li>
<li>bullet 3</li>