How-to: Customize user defined script plugin in OPS
===================================================

Customized user defined PowerShell script is now supported in OPS. User can use this feature to specify plugin scripts to run during the build process at five plugin points. Due to specify which task to run on which build step, we divided the build process into five steps: `repo_setup`, `docset_prebuild` , `docset_postbuild`, `docset_cleanup` and `repo_cleanup`. All the configuration will be set in `.openpublishing.publish.config.json`.

Step              |  Description
------------------|---------------------------------------------------------------------------------------------
repo_setup        | In repository level, repository setup is the first step during build. repository setup is only available in repository level.
docset_prebuild   | For each docset, before docset build, docset prebuild will execute. docset prebuild can both set in repository level and docset level, docset level will **overwrite** repository level.
docset_postbuild  | For each docset, after docset build is finished, docset postbuild will execute. docset postbuild can both set in repository level and docset level, will **overwrite** repository level. **Recommendation usage**: in this step, we can do some work like *validate schema*, *generate PDF for docsets* or other customized work. 
docset_cleanup    | For each docset, docset cleanup is the last step which will do some cleaning work for docset. docset cleanup can both set in repository level and docset level, docset level will **overwrite** repository level. **Recommendation usage**: in this step, we can cleanup some temporary variables in docset level.
repo_celanup      | In repository level, repository cleanup is the last step in which users can do some cleaning work for repository. repository setup is only available in repository level.

In this topic, we will show how to customize user defined script to plug in. [Here is an example of customized script](https://github.com/openpublish/OP-Customized-Script-Sample).

## Customzied script plugin syntax

  ```json
  {
    "customized_tasks": [
      {
        "repo_setup": ["repo_tasks_definitions"],
        "docset_prebuild": ["global_docset_tasks_definitions"],
        "docset_postbuild": ["global_docset_tasks_definitions"],
        "docset_cleanup": ["global_docset_tasks_definitions"],
        "repo_cleanup": ["repo_tasks_definitions"]
      }
    ],
    "docsets_to_publish": [
      {
        "customized_tasks": {
          "docset_prebuild": ["partial_docset_tasks_definitions"],
          "docset_postbuild": ["partial_docset_tasks_definitions"],
          "docset_cleanup": ["partial_docset_tasks_definitions"]
        }
      }
    ]
  }
  ```

  * **repo_tasks_definitions**: Plugin customized script path in the two repository level plugin points: `repo_setup` and `repo_cleanup`.
  * **global_docset_tasks_definitions**: Configure in the global_docset_tasks_definitions applies all the docset level plugin points `docset_prebuild`, `docset_postbuild` and `docset_cleanup` to execute customized script. It is **global** configuration for docset level plugin.
  * **partial_docset_tasks_definitions**: Any configuration in the partial_docset_tasks_definitions will **override** corresponding configuration in global_docset_tasks_definitions. It is **partial** configuration for docset level plugin.


## Download script from URL in preparation step

  * If you uploaded your script to URL, you can download the target script in the preparation step in build process.

  ```json
  {
    "dependent_URLs": [
      {
        "path_to_root": "script_from_URL/Avocado.ps1",
        "url": "https://gist.githubusercontent.com/ShuaiyiWu/54babd8f703238bcf76ab7a9905f072a/raw/c0b1bab2f2a0fa332c96dd7a692c5a25d37b868d/Avocado.ps1"
      }
    ],
    "customized_tasks": [
      {
        "repo_setup": [
          "script_from_URL/Avocado.ps1"
        ]
      }
    ]
  }
  ```

  Parameter         |  Description                                    |   Example
  ------------------|-------------------------------------------------|----------------------------------------------
  url               | **REQUIRED**. URL link to download script.      |  `"url": "<script_destination>"`
  path_to_root      | **REQUIRED**. script destination after restore. |  `"path_to_root": "script_from_URL/Avocado.ps1`

## Restore Nuget package in preparation step

  * If you manage your package as a Nuget package, you can restore the target package in the preparation step in build process.

  ```json
  {
    "dependent_packages": [
      {
        "id": "OP_customized_package_id",
        "nuget_feed": "https://www.nuget.org/api/v2",
        "path_to_root": "script_from_nuget",
        "target_framework": "net45",
        "version": "1.0.0"
      }
    ],
    "customized_tasks": [
      {
        "docset_postbuild": [
          "script_from_nuget/tools/entry_point.ps1"
        ]
      }
    ]
  }
  ```

  Parameter         |  Description                                        |  Example 
  ------------------|-----------------------------------------------------|-----------------
  id                | **REQUIRED**. Nuget package id.                     |   `"id": "OP_customized_package_id"`
  nuget_feed        | **REQUIRED**. Nuget feed source, nuget will only restore package from this source.  |  `"nuget_feed": "https://www.nuget.org/api/v2"`
  version           | **REQUIRED**. Nuget package version.                |  `"version": "1.0.0"`
  path_to_root      | **REQUIRED**. package destination after restore.    |  `"path_to_root": "script_from_nuget`
  target_framework  | **OPTIONAL**. The target framework to restore.      |   `"target_framework": "net45"`

## Retrieve scripts from Cross Repository Reference

  * By Cross Repository Reference we can retrieve scripts from other repositories.
  * More detail configuration about CRR refer to: [Cross Repository Reference](cross_repository_reference.md)
  * After configuration for CRR is done(E.g. `path_to_root` is `CRR_Script`), we can execute the script from CRR like:

```json
{
  "customized_task": [
    {
      "repo_setup": [
        "CRR_Script/entrypoint.ps1"
      ]
    }
  ]
}
```

## Scenario 1: Execute a script from local repository

  Customized script configuration         |  Description   
  ----------------------------------------|---------------------------------------------------------------
  customized_task                         | **REQUIRED**. User can specify the task to run in which build step.

  * Prepare local script in repository, e.g. put customized script in the path `script_from_local/Tangerine.ps1`.
  * To config the task run in step repo_setup, update configuration to:

```json
{
  "customized_task": [
    {
      "repo_setup": [
        "script_from_local/Tangerine.ps1"
      ]
    }
  ]
}
```

## Scenario 2: Downloading from a URL

  * Prepare a PowerShell script URL link.
  * Define download task in `dependent_URLs` with both `path_to_root` and `url`.
  * To config the task run in step repo_setup, update configuration to:

```json
{
  "dependent_URLs": [
    {
      "path_to_root": "script_from_URL/Avocado.ps1",
      "url": "https://gist.githubusercontent.com/ShuaiyiWu/54babd8f703238bcf76ab7a9905f072a/raw/c0b1bab2f2a0fa332c96dd7a692c5a25d37b868d/Avocado.ps1"
    }
  ],
  "customized_tasks": [
    {
      "repo_setup": [
        "script_from_URL/Avocado.ps1"
      ]
    }
  ]
}
```

## Scenario 3: Execute a script from nuget package

  * Prepare a package feed, which can be a public feed to restore.
  * Define a nuget restore task in `dependent_packages`.
  * To config the task run in step docset_postbuild, update configuration to:

```json
{
  "dependent_packages": [
    {
      "id": "OP_customized_script_smaple",
      "nuget_feed": "https://www.nuget.org/api/v2",
      "path_to_root": "script_from_nuget",
      "target_framework": "net45",
      "version": "1.0.0"
    }
  ],
  "customized_tasks": [
    {
      "docset_postbuild": [
        "script_from_nuget/tools/entry_point.ps1"
      ]
    }
  ]
}
```

## Scenario 4: How to execute customized script for specific docset

  * There're three build steps available in `docset_customized_tasks`, they're `docset_prebuild`, `docset_postbuild` and `docset_cleanup`.
  * When tasks is configured in `docset_customized_tasks`, which will override it in `customized_tasks`.
  * Following is the sample to execute customized script for docset "customized_script_sample".

```json
{
  "docsets_to_publish": [
    {
      "docset_name": "OP_customized_script_sample",
      "docset_customized_tasks": {
        "docset_cleanup": [],
        "docset_postbuild": [],
        "docset_prebuild": [
          "script_from_nuget/tools/entry_point.ps1"
        ]
      }
    }
  ]
}
```

> [!NOTE]
> Scenario 1, 2 and 3 is also available in executing customized script for specific docset.

## Scenario 5: How to execute customized script for all the docsets

  * Prepare the same script like it in Scenario 1.
  * To config the task run in step docset_prebuild, update configuration to:

```json
{
  "customized_task": [
    {
      "docset_prebuild": [
        "script_from_local/Tangerine.ps1"
      ]
    }
  ],
  "docsets_to_publish": [
    {
      "docset_name": "document_June"
    },
    {
      "docset_name": "document_July"
    },
    {
      "docset_name": "document_Aug"
    }
  ]
}
```

  * As a result, all the docsets `document_June`, `document_July` and `document_Aug` will execute the script `Tangerine.ps1` in step `docset_prebuild`.

## Remarks: Task execution order

  ```json
  {
    "customized_tasks": [
      {
        "repo_setup": [
          "script_from_local/Apple.ps1",
          "script_from_local/Avocado.ps1",
          "script_from_local/Tangerine.ps1"
        ]
      }
    ]
  }
  ```

> [!NOTE]
> Task execution order is corresponding to the configuration. E.g., according to the sample, the order to execute tasks is "Apple.ps1", "Avocado.ps1" and "Tangerine.ps1". 

## Remarks: I/O schema for plugin scripts

  * User can retrieve the parameter `[hashtable]$parameterDictionary`, which contains three sub-dictionaries:
    
    * **Environment**: repository level and global level variables.

    Parameter              |  Description                                    |  Example 
    -----------------------|-------------------------------------------------|-----------------
    packages               | Contains all the packages restored from nuget. They're `opbuild.templates.op`, `opbuild.htmltopdftool`, `docfx.msbuild`, `opbuild.documentidgenerator`, `opbuild.gitcontributorinformationresolver`, `opbuild.schemavalidationconsole`, and `opbuild.templates.op`. |  packages = @{opbuild.templates.op = @{targetFramework, version, packageRootFolder, actualVersion} ...
    systemDefaultVariables | OPS system default variables.                   | DefaultEntryPoint, CacheFolder, LogLevel ...
    publishConfigContent   | Content retrieve from `.openpublishing.publish.config.json`. | @{need_generate_pdf=True; need_generate_intellisense=True ...
    logFile                | The report file destination.                    | ${localRepositoryDirectory}\log\report.txt 
    repositoryRoot         | Repository root path.                           | ${localRepositoryDirectory}

    * **Docset**: docset level variables.

    Parameter                        |  Description                          |  Example 
    ---------------------------------|---------------------------------------|-----------------
    docfxConfigFile                  | Destination of docfx.json file.       | ${localRepositoryDirectory}\${docsetName}\docfx.json
    docsetInfo                       | Content retrieve from `docfx.json`.   | @{docset_name=sampleDocset; build_source_folder=sampleDocset... 
    docsetBuildEntryPoint            | Docset level build entry point.       | "op"
    docsetBuildEntryPointDestination | Entry point destination.              | ${OPScriptPackageDirectory}\op.ps1

    * **Context**: communicate variables in context, user can set variable in this sub-dictionary and communicate with other scripts.

  * Logging support

    Parameter       |  Description                                           |  Example 
    ----------------|--------------------------------------------------------|-----------------
    message         | **REQUIRED**. Log message                              | `"{your_error_mssage}"`
    source          | **REQUIRED**. The file source where error happened     | `$MyInvocation.MyCommand.Definition`
    logFilePath     | **OPTIONAL**. Target log file destination              | `$ParameterDictionary.environment.logFile`

    ```powershell

    # logging into generated report
    Logging -message 'message' -source 'source'

    ```
