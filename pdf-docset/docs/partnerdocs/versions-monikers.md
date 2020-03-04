# Reference Versioning & Monikers

To display different versions in reference content our team implemented versioning through monikers. 

## Introduction: Definitions

First, what’s a moniker? 

For [docs.microsoft.com](https://docs.microsoft.com), a **moniker** represents an abstract concept that represents a shippable unit in the product world. You can think of a moniker as a string that identifies a product that Microsoft shipped to the public, such as the .NET Framework version 4.6.2, the Azure Batch NuGet package, or the Cognitive Toolkit Python package. 

A moniker is a non-parseable unit, which means that on our service side we are not trying to interpret it in any way - it's a static string that gives a product an identifier - no more, no less. If you intend to read the moniker and understand the underlying infrastructure in any way, you are probably going around the problem the wrong way.

For the average docs consumer, the only place they will ever see a moniker is the page URL, under the `?view=` parameter assigned to it, such as:

```
https://docs.microsoft.com/en-us/dotnet/api/?view=netframework-4.6.2
```

The above URL goes to the .NET API Browser, scoped to only show APIs that are included in .NET 4.6.2.

Similarly, an individual API page can include the view parameter to show a specific version of the API.

```

Format:
https://{host_name}/{base_path}/{asset_id}?view={moniker_name}

Sample:
https://docs.microsoft.com/dotnet/system.string?view=net-framework-4.5
https://docs.microsoft.com/dotnet/system.string?view=net-framework-4.7
```

## Versioning and Moniker: Currently Supported Languages

We have support for the following languages:
* PowerShell
* Node
* Python
* .NET

Coming soon:
* Azure CLI
* REST (Swagger)
* Java

## Notes About Conceptual Versioning
Conceptual versioning is coming, we will provide a link here with more info soon.

## How to define new monikers

If you or your partner team is working on a product that has an associated version or release, chances are at some point you will need a **moniker** specifically tailored for it. There is a number of guidelines you need to keep in mind when coming up with a moniker:

* The moniker should be _relatively_ readable. This means that you need to try to avoid using convoluted abbreviations, numbering schemes that are not descriptive of the products.
* Avoid using any internal or code names within moniker names. Anything that is not customer-facing should not have a moniker associated with.
* Moniker is set-once-and-forget. This means that once it's live, you should not be editing it, adding stuff to it or removing anything is generally a bad idea because it will break a whole bunch of links and service bindings. Think carefully when you need to create a new moniker.
* General structure should follow the pattern: `product-platform-version`. As an example, for Cognitive Toolkit, we can have `cntk-py-2.0.0`. For monikers that were already created, this guideline might not apply, but moving forward we should blanket-cover the new monikers with this requirement.
* Not everyone can create a moniker. We have a **Moniker Management Group** - a number of people who can create a new moniker on the backend. You can contact them at [mgmt@service.microsoft.com](mailto:mgmt@service.microsoft.com). The reason for this is because we don't want to randomize monikers, and want to uphold a certain level of quality for those.
* Keep it short. If your product is Windows Vista Ultimate Edition 2017 Media Pack, you probably need to reduce it to something like `winvista-2017-mp`.

## How to request new monikers

You have determined what moniker what you want - now you need to have it actually created. To do that, all you need to do is ping the [Moniker Management Group](mailto:mgmt@service.microsoft.com). They will help determine whether the moniker is good and needs some tweaks. If all goes well, you should have your moniker created within a couple of minutes - once it's in the DHS (Docs Hosting Service) and the API Browser moniker service, you can instantly start using it in your docset.

## Modifying/Deleting a Moniker Once It's Live 

You should never do that. Think it through when you are creating it. We can mark a moniker as deprecated, but you should generally never delete/edit them as long as the content associated with those is live anywhere on [docs.microsoft.com](https://docs.microsoft.com).

## Associating Monikers with Content

Depending on the content target, moniker associations might be different. 

Before learning how to use moniker, it is important for users to know that there are two kinds of moniker mechanism. Both of them can be used to organize git repository content. One is separate moniker and another is combined.

### Separate moniker
Separate moniker mechanism is usually used when content among different monikers has relatively large differences. The way to use separate moniker is related to docfx configuration. Here’s a sample of configuration of docfx.json:

```json
{
  "build": {
    "content": [
      {
        "files": [
          "**/*.yml",
          "**/*.md"
        ],
        "src": "azadps-2.0.0.52-src",
        "version": "azadps-2.0.0.52",
        "exclude": [
          "**/includes/**"
        ]
      },
      {
        "files": [
          "**/*.yml",
          "**/*.md"
        ],
        "src": "azipps-1.3.155.2-src",
        "version": "azipps-1.3.155.2",
        "exclude": [
          "**/includes/**"
        ]
      }
    ],
    "versions": {
      "azadps-2.0.0.52": {
        "dest": "azadps-2.0.0.52-dest"
      },
      "azipps-1.3.155.2": {
        "dest": "azipps-1.3.155.2-dest"
      }
    }
  }
}
```

Explanations to the properties in **docfx.json** configuration file

- Properties in **content**
  - src: indicate the source folder of content.
  - version: indicate the version of the content.

  combine those two properties, we can conclude that content in which source folder will be built with what version 
- Properties in **versions**
  - key: represent for the version, which is related to the property **version** in **content**
  - dest: dest subfolder of version. It decides the subfolder of build result with specified version to be put.

In above case, if there's a markdown file *a.md* in folder *azadps-2.0.0.52-src*. Afater building, the result page "a.html" will have version *azadps-2.0.0.52* be put under *{dest_folder}/azadps-2.0.0.52-dest* folder.

> [!IMPORTANT]
> In OPS, you can't use any version you want. The version should be provisioned in OPS at first.  
> For now as there's no way for user to provision version. So if necessary, please contact with DHS team to add version.

> [!TIP]
> OPS moniker has its naming rule. It must match the regrex `^[a-zA-Z][a-zA-Z0-9]{1,16}[-]{1}[a-zA-Z0-9.-]{0,12}[^.]+$`

### Combined moniker
Combined moniker is usually used when content among different monikers are similar.

#### Configure combined moniker
If user want to use combined moniker, no change is needed in **docfx.json** configuraiton file. User can just specify the monikers in article's yaml header to indicate the article has more than one monikers.  

For example if a markdown file has two monikers *azadps-2.0.0.52* and *azipps-1.3.155.2*, then in yaml header user can specify a property like following shows:

```yaml
- monikers
  - azadps-2.0.0.52
  - azipps-1.3.155.2
```

Besides, to make combined monier work, user should add more information of docset in [open pulbishing configuration file](publish-configuration.md). That information is used to tell OPS how many monikers the docset has. 

For example, in this case, the configuration file should like following shows:
```json
  "docsets_to_publish": [
    {
      "docset_name": "my_docset",
      "build_source_folder": "src",
      "build_output_subfolder": "out_sub",
      "locale": "en-us",
      "monikers": ["azadps-2.0.0.52", "azipps-1.3.155.2"],
      "open_to_public_contributors": true,
      "type_mapping": {
        "Conceptual": "Content",
        "ManagedReference": "Content",
        "RestApi": "Content"
      },
      "build_entry_point": "docs",
      "template_folder": "_themes"
    }
  ]
```

The value of **monikers** property in configuration represents for all the monikers of this docset. User should combine and list all the monikers the content used here.

> [!WARNING]
> - If you only set monikers in documentations but not in op configuration file, then your docset won't be regarded as a moniker docset.
>   That means when you visit the page, it won't show any moniker selector on the page.
> - If you set *azadps-2.0.0.52* and *azipps-1.3.155.2* in documentations, however only set one moniker such as *azipps-1.3.155.2* in op configuration file.
>   Then the final page will only show moniker *azipps-1.3.155.2* in moniker selector but no moniker *azadps-2.0.0.52*.  
>   That's the reason why combined moniker you should set all monikers in op configuration file.

#### Combined moniker syntax in markdown content
Comming soon...

## Moniker Order
Different versions of a product are mapping to different monikers. For users who prefers to see the **tip** version, currently we define the **tip** moniker as:

- The latest version which is **not prerelease** and **not deprecated**.
- If not found, select the latest version which is **prerelease**.
- If not found, select the latest version which is **deprecated**.

> [NOTE]
> We use an *Order* property on moniker to define which is the latest version. Now all the orders are set manually, e.g., 'netframework-4.5' ----> 450, 'netframework-4.5.1' ----> 451.
> How to determine the *Order* when provisioning a moniker is still under design.
