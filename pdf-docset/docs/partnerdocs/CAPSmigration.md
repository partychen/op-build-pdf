# Migrate content from CAPS using Markdown Exporter Tool

---
author: sudeepku
---
## Overview 
To migrate your CAPS content to OPS, the CAPS content must be exported to your git repository. The CAPS MarkdownExporter.exe is a self-serve command-line tool used to export CAPS content, including images and tokens. This article walks you through using the CAPS MarkdownExporter tool to export your content out of CAPS into your git repo.

### Prerequisites

1. Using the CAPS Markdown Exporter Tool requires that your content in CAPS is already in the markdown format.
  * If it is not, please follow first the instructions [here (corpnet only)](https://msdnstage-ppe.redmond.corp.microsoft.com/en-US/library/mt918021(MSDN.10).aspx).
  * In case you need it, you can also look at our internal documentation [here](https://microsoft.sharepoint.com/teams/Visual_Studio_China/_layouts/15/WopiFrame2.aspx?sourcedoc=%7b824ce5b2-baea-4bca-a196-de481d3c223b%7d&action=edit&wd=target%28OPS%20Migration%2Eone%7CD089CC75-1569-4B69-BF8D-235EA7E5ACD1%2F%29) 
2. You already have a git repository created and have write permissions to it. Your own fork of the actual repo or a test repo is fine as well. 

## <a name="define-content-organization-in-target-repo"></a>Step 1 - Define your content organization in target repository
Before you begin to export content from CAPS, you need to have a clear defintion of how your content is going to be organized in the target 
repo. A well planned content architecture has a significant bearing on the user experience, site navigation and SEO. In the content migration context, it minimizes the need for multiple migrations and post migration cleanup effort such as fixing broken links and references.
Please refer to the CSI guidance on [Content Navigation and Architecture Design](https://ppe.msdn.microsoft.com/en-us/ce-csi-docs/docs-style/style-guide-navigation-architecture-design?branch=master).
Although this guidance is tailored to docs.microsoft.com experience, most of it is applicable to other 
rendering sites (Technet, MSDN etc.) as well. 

### 1.1 Minimum content IA needed for markdown Export 
You will need at least **Folder/sub-folder structure in the target repo** defined.
The example below shows content structure from WindowsServer repo.
![[sample content structure]](../images/markdown-export/repo-content-structure.png)
 
## Step 2 - Create queries in CAPS 
Once you have defined the content organization in the target repository, the next step is to define the quries in CAPS to identify the content to be exported.
### <a name="first-time-export"></a>2.1 First time export 
Create your queries in CAPS as below.

1. Create a query folder structure : Shared Queries--> OPS_Migration-->Repo Name-->export-folder-name
2. Create queries which contain the topics for each folder/sub-folder as defined in your content organization explained in [Step 1](#define-content-organization-in-target-repo).
3. Save your queries exactly as the directory path in your target repo. 
4. Copy the query container URL. You will need this for Markdown Tool Exporter configuration.

> [!NOTE]
> The export-folder-name in step 1 is just a friendly name. It is the Query container URL which uniquely defines where your export queries are at the exporter tool runtime.
> It has no bearing on where the content is exported. The query names do determine the relative folder path in the repo where the topics will be created.

Using the same content organization as illustrated in [Step 1](#define-content-organization-in-target-repo). The example below, shows content structure from WindowsServer repo.
![[sample CAPS query structure]](../images/markdown-export/caps-query-structure.png)

### 2.2 Delta (second and subsequent) exports 
OPS onboarding can take several weeks depending on the size and complexity of your portfolio. While onboarding is in progress,
content teams often need to update content in CAPS for critical content fixes.
In such cases, you would want to run a delta export to capture the changes since the last export.
For running a delta export, you would follow the same steps to construct the queries as in [First time export](#first-time-export), with the following additinal steps:

1. review your previous queries and add "ContentModifiedDate" filter to capture only those topics which have changed since the last export.
2. save your queries (save as) in a new query folder say, 'delta-export-mm-dd-yy'. 
3. copy the query container URL for the new query folder. 

### 2.3 Check and update your topics in the export queries
Please verify and update the topics in each of your queries for
1. Writer Name. If the writers have moved teams, assign new owners/writers to the topics.
2. metadata - ensure the metadata is upto date and accurate in CAPS before you export. 
Following metadata fields are exported by the markdown exporter if defined.
 ![[metadata fields exported from CAPS]](../images/markdown-export/caps-metadata-exported-to-ops.png)

Use the CAPS bulkupdate tool to update metadata for topics in your export queries as necessary.
Refer to [Managing metadata in content for CSI](https://ppe.msdn.microsoft.com/en-us/ce-csi-docs/ops/ops-onboarding/managing-content/content-meta-data?branch=master) for CSI metadata requirements for content published through OPS.

## Step 3 Run the Markdown Exporter Tool 
### 3.1Requirements
Windows Operating System: Windows 10, 8.1, Server 2012 etc.
### 3.2 Install the tool 
The tool is a clickOnce application and you should only need to install it once.  The tool will auto update when new versions are available. 
1. Copy the "SampleConfiguration" folder from [\\rr1dx2tpehost01\MigrationToolsDrop\MarkdownExporter_ClickOnce](file://rr1dx2tpehost01/MigrationToolsDrop/MarkdownExporter_ClickOnce) to your local drive and rename as desired, for example "c:\ExporterConfiguration"
2. Run **setup.exe** from [\\rr1dx2tpehost01\MigrationToolsDrop\MarkdownExporter_ClickOnce](file://rr1dx2tpehost01/MigrationToolsDrop/MarkdownExporter_ClickOnce)

### 3.3 configure your export settings 
Markdown Exporter requires the following two json configuration files. They were in the "SampleConfiguration" folder you copied in a previous step.
- GithubAccount.json
- MigrationInfo_en-us.json

#### 3.3.1 Update the Writer to GitHub account map (`GithubAccount.json`) 
you need to map writers Names to their corresponding github account Id. This is needed to export the content attributions to the rightful content owner.

1. Go to the local folder where you copied the sample configuration files, for example "c:\ExporterConfiguration".
2. Open the `GithubAccount.json` file in a text editor. Visual Studio code is also a good editor for json file.s
3. Update the entries for writers for your topics in your queries. 
4. You can map a GitId of a new content owner if the old content owner is not with the team.
5. Save the updated mappings file in the same location

the following is a sample account mappping file:

```
{
"Bill Anderson":"bandersmsft",
"Bill Mathers":"billmath",
"Brian Wren":"bwren",
"Brit Weston":"britw",
"Carmon Mills":"carmonmills",
"Catherine Watson":"cwatsonmsft",
"Charles Freeman":"cfreemanwa",
"Corey Plett":"coreyp",
"Cynthia Nottingham":"jpjofre",
"Femila Anilkumar":"Femila"
}

```
In the next step, you will edit the main configuration file (`MigrationInfo_en-us.json`)to point to the location and file name of your local `GithubAccount.json`.

>[!WARNING]
> If you do not update the Writer Name <--> GitId map, the exporter will not export the ms.author attribute correctly. You may have wrong author attribution on the published pages

#### <a name="configure_migration_settings"></a>3.3.2 Define the Migration Settings for your export (`MigrationInfo_en-us.json`)

This step lets you define and configure your export settings and options

1. Go to the local folder where you copied the sample configuration files, for example "c:\ExporterConfiguration".
2. Open the sample configuration file , `MigrationInfo_en-us.json` in a text editor.
3. Update the settings as described below
4. Save the file with a different name e.g `c:\ExporterConfiguration\SystemCenter-delta-export-migrationInfo.json`. 



|Config Parameter| Description| Example|comments| 
|-----------------------|------------|---------------|-------|
|CapsQueryFolderUrl|query container URL for your CAPS query folder|see the sample config file below||
|Locale| language/locale topics you want to export|en-US| content export for other locales is in works. Not supported currently.|
|GitUserName| your user name on github. different from GitId | Sudeep Kumar||
|GitEmail| email associated with your account on github.|| actually the tool does not care much|
|GitAccessToken| your git access token |f50bb55d-b80f-4151-bc3c-dd01cad61917|This is needed. See GitHub help on [how to create an access token](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) |
|GitRepoName| This is the Git repo name |WindowsServerDocs-pr|Your query sub-folder name in CAPS should be same as this field value|
|GitBasePath| folder in your repo under which all the content will be exported|WindowsServerDocs|This is typically the provisoned docset folder|
|GitWorkingBranch|git branch in which you want to run the export|migration|you can choose to run the export in the master branch for the first time export|
|GitLocalDirectory| path to my local clone of the repo|c:\\git\\sudeepku\\WindowServerDocs-pr|please escape backward slashes. see example below.|
|AutoPushToRemote|pushes the exported content to remote if set to true (origin)|false|recommended to keep the default. Allows you to verify export locally first|
|FlattenToken|if true, tokens will be replaced with the string value of the token in the source CAPS portfolio.  |
|TagMigrated| **Only set this to true** when you are ready for the production migration.  This option will add a tag to each topic in CAPS "en-us to ops" to indicate to the loc team the topic has been exported and will no longer be edited in CAPS.|
|TokenTargetFolderName|folder name for tokens|includes|This is generated as a sub-folder for each export query you defined in CAPS. Default is the CSI team recommended name|
|ImageTargetFolderName|folder name for images|media|This is generated as a sub-folder for each export query you defined in CAPS. Default is the CSI team recommended name|
|Mode| run the tool in preview or export mode.|"perview", "export", or "gentree"| running the tool in preview mode, generates a File Map report, which you can use to change file names in destination. "gentree" mode generates structuredtoc.md files based on the export queries, which can then be reference from TOC.md to easily build a structured TOC.|
|TopicNameMappingFile| location of the file name mapping containinng filename overrides||specify complete file path if you are specifying file name overrides|
|SiteName|The name of the site to publish to.|Microsoft Docs|Appends the site identifier, such as " | Microsoft Docs" to every topic title for SEO. Currently only None (default) and Microsoft Docs are supported.|
|DependentFileNameMappings|Dictionary of related repos and mapping files.|{"testCrossReference": "C:\\csharpvb.xlsx"}|Specify related repos and their topic name mapping files to resolve cross-repo links.|
```
{
  "CapsQueryFolderUrl": "https://devint.microsoftonedoc.com/#/organizations/ffabd50649854ead8b30a42798aeb2ed/projects/bf276c8e-0d64-48fe-8e6e-27c51b445f93/containers/ebd7b3bb-81cf-4776-8daf-b08cc8062c93",
  // this is the query container URL which contains all querries for your export.
  "Locale": "en-US",
  "GitUserName": "your name",
  "GitEmail": "youremail@microsoft.com",
  "GitAccessToken": "put your git access token here",
  "GitRepoName": "WindowsServerDocs-pr", //This is the Git repo name and should be same as the query sub-folder name in CAPS. Refer to step 2
  "GitBasePath": "WindowsServerDocs",  // this is the the folder in your repo under which the content will be exported.This is generally the provisioned Folder (docset) in your repo
  "GitWorkingBranch": "migration", // the git branch in which you want to run the export
  "GitLocalDirectory": "D:\\git\\sudeepku\\WindowServerDocs-pr", // path to my local clone of the repo
  "AutoPushToRemote": false, // whether you want to push the exported content to remote (origin)
  "FlattenToken": false, //If True, tokens are replaced with the literal values from the source CAPS portfolio.
  "TagMigrated": false, //Will set "en-us to ops" on CAPS topics-> tags metadata after migration done if this is true. 
  "TokenTargetFolderName": "includes",  // folder name for tokens. This is generated as a sub-folder for each export query you defined in CAPSDefault is the CSI team recommneded name
  "ImageTargetFolderName": "media"  //  folder name for images. This is generated as a sub-folder for each export query you defined in CAPS. Default is the CSI team recommended name. 
  "Mode": "export", // required, the supported mode: preview, export, gentree
  "TopicNameMappingFile": "C:\\CAPS\\Migration\\ExportFileMap_EMS_MD_07281203.xlsx", // mapping file containing filename overrides
  "SiteName": "Microsoft Docs", //Right now only support none, Microsoft Docs  
  "DependentFileNameMappings": {"testCrossReference": "C:\\csharpvb.xlsx"} // point to related repos and their topic name mapping files to resolve cross repo links
}
```

>[!TIP]
>Keeping your migration settings in the same location (step 5) above will come handy if you need to run multiple exports.


### 3.4 Prepare a local clone of the repo
Markdown exporter tool requires you beforehand prepare a local directory cloned from the remote git repo you want to export to.
On gitbash console, run the clone command, for example: 
```
git clone https://github.com/Microsoft/WindowsServerDocs-pr.git
```
![[Create a clone of your target repo]](../images/markdown-export/git-clone-command.png)

### <a name="run_tool"></a>3.5 Run the tool 
First decide what **Mode** you want to run the tool in; "preview", "export", or "gentree" mode and update the configuration as needed.
You are now ready to run the tool. Becasue the tool is a click-once applicaiton it auto updates and installs to a different location each time.  There are two approaches to run the tool.
#### 3.5.1 from the Start Menue
1. The tool instllation adds a shortcut to the Start Menu so the easiest way to run the tool is to click the Windows start icon and type "Markd" and click the "MarkdownExporter".  
2. The application will open and prompt for the path to your configuration file.

#### 3.5.2 manuall call the exe and provide a configuration file path.
The shortcut installs to a standard location, for example
`C:\Users\craigg\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\MarkdownExporter
MarkdownExporter.exe`
1. Open cmd prompt (admin mode preferred)
2. Switch to the MarkdownExporter linktool directory. For example:
`cd C:\Users\craigg\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\MarkdownExporter`
3. run the exe and provide the path to the configuration file.  For example:
`MarkdownExporter.exe C:\Tools\MarkdownExporter\Configuration_craig\MigrationInfo_sqldrivers.json`
4. Verify setting. The tool will show you configuration information before migration started. Please input 'y' if configuration is correct.
 ![[verify the settings]](../images/markdown-export/markdown-exporter-confirmation-cmd.PNG)
5. If you ran the tool in "export" mode it will start migrating images, tokens and topics. If you ran it in the "preview" mode , it generates a ExportFileMap under the "report" folder of the tool.
6. Once the tool has succesfully completed, it will print a message in the command prompt. Press any key to exit the tool.

>[!TIP]
>Allow the tool to run for 5-15 minutes depending on the size of the queries. If the export is going to fail, it will likely fail fast. 

### 3.6 Preview Mode and file name overrides 
The exporter tool allows you to run the tool in "preview" mode to generate a list of all topics, their default file names and the directory path. You have an option, to override the default file names and run the tool in "export" mode.
You may need to override default file names in cases where the file name is too long ( windows limits the max name of a file to 260 chars), or for SEO reasons e.g remove common words like a,an,the,in etc.
Steps to run the tool in preview mode and export with file name overrides.

1. Update the "Mode" parameter to "preview"  in the [configuration file](#configure_migration_settings).
2. Run the tool following the steps in the [preceding section](#run_tool).
3. Go to the tool "install directory"/report folder and open the ExportFileMap_portfolioname_datetime.xlsx 
4. Review the file names and provide alternate(override) file name in the "RevisedFileName" coloumn.
5. Save this file (either at the same location or at an alternate location)
6. Update the TopicNameMappingFile property in the configuration to the updated ExportFileMap. 
7. Change the Mode property to  "export" in the tool configuration.
7. Run the Exporter tool again with udpated config. 


### <a name="verify_export"></a>3.7. Verify Export 

1. Go to the <Markdown Exporter install directory>/report folder.
2. Locate the excel report (format Migration_caps_porfolioname_locale_datetime.xlsx) from the current run and and review the export report (multiple sheets) to see if there were errors/warnings in the export.
3. Fix the issues with the topics in CAPS and run the export again if needed.
4. Run a local OPS Build to identify other build relates issues. See [Local builds and preview](local-build-and-preview.md) for instructions.

### 3.8 TOC file generated after export 

The exporter file will generate a TOC.md file. This TOC file is a flat list with all the topics exported. In most cases,

1. you would re-arrange the TOC , add multiple levels to the flat list or re-organize the topics.
2. If you are running the export in batches , you will need to re-concile TOCs generated after each export.
3. OPS provides multiple ways to organize and manage your TOCs inclduing support for nested TOCs. Please refer to [TOC Management](toc-management.md) for details.

### 3.9 Push the content to Orgin (remote)
If everything is looking good , push the content to remote .

## Known Limitations and in-progress enhancements

### In-progress enhancements


### Known limitations

1. The exporter tool does not export the TOC hirearchy as in CAPS. This is by design since the query based export has no-knowldge about the TOC for a docset.
2. If your exported topics have references to other topics which are not included in the export queries, you may end up with broken references. 
  Please refer to [Verify Export](#verify_export) section on how to review and fix these.

##  FAQs 

