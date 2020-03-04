# DiffFolder Plugin

## Basic Infomation
- Nuget Package Id: Microsoft.OpenPublishing.CommonPlugins
- Nuget Package Feed: https://www.myget.org/F/op/api/v2
- Entry Point: `tools/DiffFolder.ps1`

## Purpose
This plugin was built to monitor the changes in a folder, and translate the changes to change list for OPS. 

You only need this plugin when some of your content is generated/modified at build time, and normal Git change list cannot trace them.

## How it works
This plugin calculates md5 hash for all the files under the monitoring folder, and save the hash values in OPS cache. It compares the hash values against the last saved ones, and found out which files are added, updated or deleted. 

## Repo Configuration
Please refer to [repo configuration in Azure .Net repo](https://github.com/Azure/azure-docs-sdk-dotnet/blob/master/.openpublishing.publish.config.json) as an full example of how to enable this plugin. Some key points are described below:

1. Import the nuget package:

   ```json
    "dependent_packages": [
      {
        "id": "Microsoft.OpenPublishing.CommonPlugins",
        "nuget_feed": "https://www.myget.org/F/op/api/v2",
        "path_to_root": "_dependentPackages/CommonPlugins",
        "target_framework": "net45",
        "version": "latest"
      },
      ...
    ]
   ```
2. Configure the entry point:

   ```json
    "customized_tasks": {
      "docset_prebuild": [
        ...
        "_dependentPackages/CommonPlugins/tools/DiffFolder.ps1",
        ...
      ],
   ```
3. Setup DiffFolder to monitor api folder (all the path and url below are only FYI, they should be different in every repo):

   ```json
    "DiffFolder": [
      "api"
    ]
   ```