# Build Configuration specifics for localized repos (docfx.json)

This topic contains information about how to enable or fix build configuration for localized repos.

## Include Xref dependencies package

[Example 1](https://github.com/dotnet/docs.de-de/commit/efa0a4205a2bc410a2d6f954c0093852df8358a1)

[Example 1](https://github.com/MicrosoftDocs/visualstudio-docs-pr.ja-jp/commit/d775aefff4b06e821e727b956efd8b8db848ecc3) 

```
"xref": [
      "dotnet-xref/_zip/dotnet.zip",
      "dotnet-xref/_zip/vs.110.zip",
      "dotnet-xref/_zip/vs.140.zip",
      "dotnet-xref/_zip/office15.zip",
      "dotnet-xref/_zip/missingapi.yml",
      "dotnet-xref/_zip/msdnsmallset.yml"
    ]
```

## Changing CRR to using Yml4Loc instead of CoreApi.git 
[Example](https://github.com/dotnet/docs.de-de/commit/26facd4e7f53e2a8e1f9deae37c3359a550b4bd5)

## Side by side configuration
If the localization team needs side by side configuration, update the following. [Example](https://github.com/MicrosoftDocs/CloudAppSecurityDocs-pr.pt-br/pull/1/files)

```
 "globalMetadata": {
      "bilingual_type": "hover over"
    }
```

## Bredcrumb
Follow the same steps than English for [breadcrumb](breadcrumb.md).

## Excluding a set of files or a folder for build
We are localizing files from /live branch of the en-US azure-docs repo; and the localized files go straight to the /live branch of the loc repos and get published.  If the en-us team wants to simultaneously ship content from one subfolder of the repo for all languages (e.g. files in this folder https://github.com/MicrosoftDocs/azure-docs-pr/tree/master/articles/service-fabric), is it possible to exclude the folder from DocFX, or otherwise prevent just files from this one folder from publishing for a short time (e.g. 2 weeks)?  All other files need to continue to publish. This would enable loc to catch up with translations without having to change the OpenLoc hookup.

We can exclude a set of files or a folder from build and publish in docfx.json, see [build configuration](build-configuration.md) for details. 

Note that the excluded contents will be deleted from the end point. So if you are doing this for localization, then your content will default back to English.
