# Yaml Localizable Properties Configuration

## 1. 3 Options of Localizable Property Filter: 

Option | Localizable Property Filter| Model reference
-------|----------------------------|----------------
General | description", "search.keyword", "title", "h1", "name", "keywords" | -
MRef | "summary", "description", "remarks" | [https://github.com/dotnet/docfx/blob/dev/src/Microsoft.DocAsCode.DataContracts.ManagedReference/ItemViewModel.cs](https://github.com/dotnet/docfx/blob/dev/src/Microsoft.DocAsCode.DataContracts.ManagedReference/ItemViewModel.cs)
Powershell/Cmdlet | - | 

## 2. How to configure in OL: `yamlFilter`

In localization_config.json

```	
{
  "locales": [ "fr-fr", "ko-kr" ],
  "files": [
  	"!coreapi/excluded/*.yml",
	   "coreapi/**/*.yml"
  ],
  "dontDeleteFiles": true,
  "includeDependencies": true,
  "autoPush": true,
  "xliffVersion": "2.0",
  "useJavascriptMarkdownTransformer": true,
  "createHandoffFilePerLocale": false,
  "markdownTransformerOptions": {
              "yamlFilter": "mref"
  }
}
```
