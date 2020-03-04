---
f1_keywords:
- samplef1keyword1
- samplef1keyword2
dev_langs:
- csharp
- fsharp
---

# How To Publish Content to Enable F1 Query

## Metadata Strategy
1. **f1_keywords** (_optional_, _multivalue_): **This metadata is mandatory for F1 Query.** Need to provide one or more F1 keywords for this content, which will be used to match the keywords from F1 query URL.

2. **dev_langs** (_optional_, _multivalue_): **This metadata is optional for F1 Query.** The supported develop languages of this content. The F1 query will specify the dev_lang that the developer is currently using in the IDE. 


##YAML Header
The metadata is set in YAML header of the Markdown file of your content:

```
md
f1_keywords:
- samplef1keyword1
- samplef1keyword2
dev_langs:
- csharp
- fsharp
```

##Examples:

[Example1](https://github.com/Microsoft/visualstudio-docs/blob/master/docs/ide/reference/find-and-replace-environment-options-dialog-box.md)
![F1Example1](media/F1Example1.jpg)

[Example2](https://github.com/Microsoft/cpp-docs/blob/master/docs/atl/com-modules-classes.md)
![F1Example2](media/F1Example2.jpg)