# Publish Configuration specifics for localized repos (.openpublishing.publish.config.json)



## Enabling PDF
You can enable the PDF by following the same instructions than for [English PDF configuration](publish-configuration.md#enable-pdf). 

Note that alike docs templates, the template repo for PDF is language agnostic. I.e., under `"dependent_repositories"`, you keep this reference like English:

```  
  {
    "path_to_root": "_themes.pdf",
    "url": "https://github.com/Microsoft/templates.docs.msft.pdf",
    "branch": "master"
  }
```

## Adding English as locale fallback during build
If there are files that are missing during build, such as tokens, images, etc. you can add English repo as the default back to avoid broken items as a dependent repository. [Example](https://github.com/dotnet/docs.de-de/commit/8e65d313aa163b1c57bb0322bc45d9bc7f63da8e):

```
"dependent_repositories": [
 
    {
      "path_to_root": "_repo.en-us",
      "url": "https://github.com/dotnet/docs",
      "branch": "live"
    }
  ]
```

## Referring to English codesnippet repository
Code snippets do not get localized, so you simply need to reference to the code snippet repo for your release as a dependent repository. Simply mimic the refence in the English repo. [Example](https://github.com/dotnet/docs.de-de/commit/8e65d313aa163b1c57bb0322bc45d9bc7f63da8e):

```
"dependent_repositories": [
    {
      "path_to_root": "api_ref",
      "url": "https://github.com/docascode/coreapi.git",
      "branch": "master"
    }
  ]
```

## CRR of Xref
[Example](https://github.com/dotnet/docs.de-de/commit/144ce829340dd2afb655bea0dc8eeca952c7fead)

```
"dependent_repositories": [
    {
      "path_to_root": "dotnet-xref",
      "url": "https://github.com/MicrosoftDocs/dotnet-xref",
      "branch": "live",
      "branch_mapping":
      {
        "master": "master",
        "live": "live"
      }
    }
  ]
```

## Add Monikers
Your repo might require one or multiple monikers. If so, you should copy the following section from the English configuration file. [Example](https://github.com/dotnet/docs.de-de/commit/1824172594b812bdea9db81032e8c3ec53500d6b)

```
  "docsets_to_publish": [
    {
    ...
      "monikers": [
        "netframework-4.5.1",
        "netframework-4.5.2",
        "netframework-4.5",
        "netframework-4.6",
        "netframework-4.6.1",
        "netframework-4.6.2",
        "netframework-4.7",
        "netcore-1.0",
        "netcore-1.1",
        "netcore-2.0",
        "netstandard-1.0",
        "netstandard-1.1",
        "netstandard-1.2",
        "netstandard-1.3",
        "netstandard-1.4",
        "netstandard-1.5",
        "netstandard-1.6",
        "netstandard-2.0",
        "xamarinios-10.8",
        "xamarinandroid-7.1",
        "xamarinmac-3.0"
      ],
```

## Changing CRR to using Yml4Loc instead of CoreApi.git

[Example](https://github.com/dotnet/docs.de-de/commit/1824172594b812bdea9db81032e8c3ec53500d6b)

```
"dependent_repositories": [
    {
      "path_to_root": "api",
      "url": "https://github.com/MicrosoftDocs/dotnet-docs-yml4loc",
      "branch": "master"
    }
  ]
  
```

## Add plugin dependent packages

Copy the following section from the English configuration file. [Example](https://github.com/dotnet/docs.de-de/commit/1824172594b812bdea9db81032e8c3ec53500d6b)
```
      "customized_template_paths": [
        "_dependentPackages/memberpage.plugins/content"
      ]
```

``` 
  "dependent_packages": [
    {
      "id": "memberpage.plugins",
      "nuget_feed": "https://www.myget.org/F/docfx/api/v2",
      "path_to_root": "_dependentPackages/memberpage.plugins",
      "target_framework": "net45",
      "version": "latest"
    }
  ]
```
[Example](https://github.com/dotnet/docs.de-de/commit/1824172594b812bdea9db81032e8c3ec53500d6b)

## Changing from MSDN/TN to Docs or static to dynamic rendering
If the configuration does not work in OPS portal, and you see your content as garbage, make the following changes.
[Example](https://github.com/MicrosoftDocs/SystemCenterDocs-pr.zh-tw/pull/3/files) 

```
  "docsets_to_publish": [
    {
      "monikers": [],
      },
```

```
      "build_entry_point": "docs",
      "template_folder": "_themes",
      "version": 0
```

```
  "dependent_repositories": [
    {
      "path_to_root": "_themes",
      "url": "https://github.com/Microsoft/templates.docs.msft.zh-tw",
      "branch": "master",
      "branch_mapping": {}
    }
  ]
```

