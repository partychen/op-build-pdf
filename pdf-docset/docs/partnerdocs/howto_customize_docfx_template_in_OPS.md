How-to: Customize DocFx template in OPS
=======================================

DocFx customzied template is now supported in OPS. User can use this feature to specify customized Docfx template for docset. **local template**, **template cloned from CRR**, **template restored from Nuget package** and **template in another repository** is available.

## Syntax in configuration file

User can specify a property with name `"customized_template_paths"` under one docset in the configuration file. The value should be a string array. **Any string value inside the property is a relative path to the repository root.** User should make sure the path is existed. There're four ways to allow user to prepare the template folder as below.

Configuration syntax:

```json
{
  "docsets_to_publish": [
    {
      "docset_name": "<docset_name>",
      "customized_template_paths": [
        "<template_folder1_path_to_repository_root>",
        "<template_folder2_path_to_repository_root>"
      ]      
    }
  ]
}
```

### DocFx plugins

DocFx can have plugins for both **page style** and **validation rule**. However, validation rule need to be complied in `plugin.dll`, which should be put inside a `plugins` folder under the specified path.

#### Template for DocFx customized page style

* User can prepare page style files in template folder, such as `.js` and `.tmpl` files.

#### Template for DocFx validation rule

* Create the subfolder with name `plugins` under template folder.
* Add metadata in plugin.
* Add validation rule for validating metadata in plugin.

## How to prepare template folder

Similar with [Customize user defined script plugin in OPS](howto_customize_user_defined_script_plugin_in_OPS.md). User can either apply existed template folder, CRR, nuget or URL to prepare template folder.

### Existed template folder

* Prepare local template folder, e.g. put your template folder in the path `localTemplate/op.html`.
* Configure the template by specifying the value in `customized_template_paths` property under `docsets_to_publish`.
* Sample configuration refer to:

```json
{
  "docsets_to_publish": [
    {
      "docset_name": "OP-Customized-Docfx-
      Template-Sample",
      "customized_template_paths": "localTemplate/op.html"      
    }
  ]
}
```

### Use CRR to clone template folder

[CRR](cross_repository_reference.md) could also be used to prepare customize Docfx template.

- User create a repository that contains template.
- Define a CRR definition in the `dependent_repositories` property.
- Use the template in corresponding docset by specifying the value in `customized_template_paths` property.

Definition Sample:
```json
"docsets_to_publish": [
  {
    "docset_name": "fenxu_plugins_applied_repository",
    "build_source_folder": "fenxu_plugins_applied_repository",
    "build_output_subfolder": "fenxu_plugins_applied_repository",
    "locale": "en-us",
    "version": 0,
    "open_to_public_contributors": true,
    "type_mapping": {
      "Conceptual": "Content",
      "ManagedReference": "Content",
      "RestApi": "Content"
    },
    "build_entry_point": "docs",
    "template_folder": "_themes",
    "customized_template_paths": ["sample_plugins/SeparatePlugins/SeparatePlugins/output"]
  }
],
"dependent_repositories": [
  {
    "path_to_root": "sample_plugins",
    "url": "https://github.com/fenxu/fenxu_plugins_project",
    "branch": "master",
    "branch_mapping": {}
  }
]
```

> [!NOTE]
> If you want to add some Docfx plugins, then all the dlls should be put under a folder with name `plugins` and the value of customized_template_path should be the parent folder of the plugins folder.

### Use Nuget to restore template folder

* Prepare a package feed, which can be a public feed to restore.
* Define a nuget restore task in `dependent_packages`.
* Configure the template by specifying the value in `customized_template_paths` property under `docsets_to_publish`.
* Sample configuration refer to:

```json
{
  "dependent_packages": [
    {
      "id": "Docfx_sample_template",
      "nuget_feed": "https://www.nuget.org/api/v2",
      "path_to_root": "templateFromNuget",
      "target_framework": "net45",
      "version": "1.0.0"
    }
  ],
  "docsets_to_publish": [
    {
      "customized_template_paths": "templateFromNuget/templates/msdn.html",
      "docset_name": "OP-Customized-Docfx-Template-Sample"
    }
  ]
}
```

### User URL to download template file

* Prepare a URL link to download template file.
* Define download task in `dependent_URLs` with both `path_to_root` and `url`.
* Configure the template by specifying the value in `customized_template_paths` property under `docsets_to_publish`.
* Sample configuration refer to:

```json
{
  "dependent_URLs": [
    {
      "path_to_root": "templateFromUrl/hello",
      "url": "https://www.bing.com/hello.js"
    }
  ],
  "docsets_to_publish": [
    {
      "docset_name": "OP-Customized-Docfx-Template-Sample",
      "customized_template_paths": "templateFromUrl/hello"
    }
  ]
}
```

> [!TIP]
> If user want to apply local template and local preview. It is recommanded to use existing template folder in the repository. After local preview is done, user can remove these temporary template folder files if they don't want to commit.