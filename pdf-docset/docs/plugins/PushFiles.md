# PushFiles Plugin

## Basic Infomation
- Nuget Package Id: Microsoft.OpenPublishing.CommonPlugins
- Nuget Package Feed: https://www.myget.org/F/op/api/v2
- Entry Point: `tools/PushFiles.ps1`

## Purpose
This plugin was built to commit and push files to another repo at build time. It allows OPS Build to output files like a CI job.

Typical usage of this plugin includes:
- In .Net repos, the .yml files are normally not checked-in. PushFiles can be used to push the generated .yml files to another repo for localization.
- Reference repos often generates xref mapping files. PushFiles can zip and copy those mapping files to a centralized repo, so that people don't need to manually download them.

## How it works
The logic of PushFiles plugin is very simple: it first clone the target repo to local, then uses [Robocopy](https://technet.microsoft.com/en-us/library/cc733145(v=ws.11).aspx) to copy changed files and purge old files in target folder, and finally do Git commit and push if necessary. 

if `dest` configuration ends with ".zip", files will be packed into a zip package before check-in.

> [!NOTE]
> This plugin uses the same credential that OPS Build uses to build the current content repo.
> - If service account is configured for current content repo, PushFiles will use the same service account to check-in files to target repo.
> - If no service account is configured, normally the account that was used to provision current content repo will be used.

## Repo Configuration
Please refer to [repo configuration in SQL Managed Reference Repo](https://github.com/MicrosoftDocs/sql-managed-reference-pr/blob/master/.openpublishing.publish.config.json) as an full example of how to enable this plugin. Some key points are described below:

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
      "docset_postbuild": [
        ...
        "_dependentPackages/CommonPlugins/tools/PushFiles.ps1",
        ...
      ],
   ```
3. Setup PushFiles to monitor certain branches, and push changed files to target repo:

   ```json
    "PushFiles": [
      {
        "branchFilter": ["master", "live", "ymlExport"],
        "targetRepo": "https://github.com/MicrosoftDocs/sql-managed-reference-pr-yml4loc.git",
        "src": "dotnet/api",
        "dest": "/",
        "files": "*.yml *.md",
        "purge": true
      }
    ]
   ```

   - `branchFilter`: only trigger PushFiles on listed branches.
   - `targetRepo`: target repo that PushFiles check-in files to.
   - `src`: source folder, used as `<Source>` in command `robocopy <Source> <Destination> <File>`
   - `dest`: destination
     - if it's a folder, then it's used as `<Destination>` in command `robocopy <Source> <Destination> <File>`.
     - if it's a path that ends with ".zip", a temp folder will be used in robocopy command, and then the copied files will be compressed into the .zip file.
   - `files`: files filter, used as `<File>` in command `robocopy <Source> <Destination> <File>`. Multiple extensions can be seperated by space.
   - `purge`: robocopy /purge parameter, used to delete files in `dest` folder that no longer exist in `src`.