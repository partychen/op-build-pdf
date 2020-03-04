# Publish Configuration (.openpublishing.publish.config.json)

Publish configuration file contains the settings necessary for build and publish. It is used:
1. when you run [local build tool](local-build-and-preview.md) on your machine;
2. when OPS build service publishes your docsets.

## Configuration options
A template of publish configuration:
[!code-json[Main](_data/publish-configuration-template.json "template of publish configuration")]

The table below explains each key in the configuration.

> [!NOTE]
> If a key is marked as available in OPS portal, use the portal to update it instead of doing it manually in the configuration file. Using the portal will be faster and error free.
>

> [!IMPORTANT]
> Some items in publishing configuration take effect on **live** branch only. The setting of these configs in other branches does not take effect.
> See [here](#configs-that-take-effect-in-live-branch-only) for details.
>

### Configs for each branch

> [!div class="mx-tdBreakAll"]
| Key | Description & Example | Available in OPS portal? |
| --- | --------------------- | ------------------------ |
| <a name="publish-config-build_entry_point"></a>build_entry_point | <ul><li>`op` (default value), or `(leave it blank)`: run OPS tool targeted to MSDN, TechNet, or VS.com.</li><li>`docs`: run OPS tool targeted to Docs.</li></ul><br><br>Example: `"build_entry_point" : "op"` | No |
| package_version | OPS tool is versioned by NuGet packages. By default, the latest official version is used. Set this value to override the default behavior. <ul><li>`latest`, or `(leave it blank)`: use latest official version of OPS tool.</li><li>`latest-prerelease`: use latest prerelease version of OPS tool.</li><li>`{the version number of the package}`: use that specified version of OPS tool.</li></ul><br><br>Example: `"package_version" : "latest"` | No |
| <a name="publish-config-notification_subscribers"></a>notification_subscribers | Provide the emails of whom want to receive the email notification. Separate each of the users or distribution lists by a comma.<br><br>Example: `"notification_subscribers": ["fenxu@microsoft.com"]` | [Yes](edit-repo-properties.md) |
| report_severity_level | Specify the level of messages to contain in build report. Options are (ordering by severity): <ul><li>`Error`: include error messages only in build report. Error message usually hints there is an issue with content or service that blocks further processing or publishing of the contents.</li><li>`Warning`: include error and warning messages in build report. Warning message hints there is an issue that may require user attention, but the issue is non-blocking in build or publish. </li><li>`Info`: include error, warning and information messages in build report. Information message usually prints out notable information about build tool or service.</li><li>`Verbose` (default value): include all levels of messages in build report. Verbose message contains all information in build and publish process and is useful for trouble shooting.</li></ul><br><br>Example: `"report_severity_level": "Verbose"` | No |
| docsets_to_publish | **REQUIRED** A collection of docsets that need to be published. The following configurations are all configured on docset level for each docset. See below examples. | See below |
| docsets_to_publish.docset_name | **REQUIRED** Provide the name of the docset. The docset needs to provisioned on portal at first, otherwise the contents under the docset won't be published.<ul><li>For different docsets, the names should be different.</li><li>For docsets that are just different in locale or version, the names should be same. Otherwise, the fallback logic won't work.</li></ul><br><br>Example: `"docsets_to_publish": { "docset_name": "some_docset" }` | Yes, for docset creation only |
| <a name="publish-config-docsets_to_publish.build_output_subfolder"></a>docsets_to_publish.build_output_subfolder | **REQUIRED** The relative output sub folder to put the built files of the build tool. In Open Publishing service, only those put in the folder get published. Recommended value is the relative path of the folder where the docset stays.<br><br>Example: `"docsets_to_publish": { "build_output_subfolder": "openpublishing/docs" }` | No |
| docsets_to_publish.build_source_folder | The relative sub folder of the docset in the repo. Normally, this setting should share the same value of [build_output_subfolder](#publish-config-docsets_to_publish.build_output_subfolder). Default is empty which means to use the same value as [build_output_subfolder](#publish-config-docsets_to_publish.build_output_subfolder).<br><br>Example: `"docsets_to_publish": { "build_source_folder": "openpublishing/docs" }` | Yes, for docset creation only |
| docsets_to_publish.build_entry_point | Indicate how to run build for this docset. It shares the same options with [repo level setting](#publish-config-build_entry_point). <ul><li>If not specified, use the value of [repo level setting](#publish-config-build_entry_point).</li><li>If specified, overrides the value of [repo level setting](#publish-config-build_entry_point) for this docset.</li></ul><br><br>Example: `"docsets_to_publish": { "build_entry_point": "docs" }` | [Yes](edit-docset-properties.md) |
| docsets_to_publish.monikers | Monikers of current docset content. **The moniker user want to specified should be provisioned in OPS at first**.<br><br>Example: `"docsets_to_publish": { "monikers": ["v1.0", "v2.0"] }` | No |
| docsets_to_publish.locale | **REQUIRED** Locale for the docset. Configure it via the portal.<br><br>Example: `"docsets_to_publish": { "locale": "en-us" }` | Yes, at docset creation. |
| docsets_to_publish.type_mapping | **REQUIRED** Internal used configuration. Should use the values shown in example.<br><br>Example:<br>`"docsets_to_publish": { "type_mapping": { "Conceptual": "Content", "ManagedReference": "Content", "RestApi": "Content" } }` | No |
| <a name="publish-config-docsets_to_publish.open_to_public_contributors"></a>docsets_to_publish.open_to_public_contributors | <ul><li>`True` (default for public repos): if you want your customers to contribute to the content. There would be a button showing on the rendered page which directs external users to a repository to submit their pull requests.</li><li>`False` (default for private repos): if you do not want your customers to contribute to the content.</li></ul><br><br>Example: `"docsets_to_publish": { "open_to_public_contributors": true }` | [Yes](edit-repo-properties.md) |
| git_repository_url_open_to_public_contributors | It is used to generate content Git URL (contribute-to link) in published page. If [open_to_public_contributors](#publish-config-docsets_to_publish.open_to_public_contributors) is set to true for any docset in the repo, this config needs to be defined. It can be the same Git repo if the whole project is public. It can also be a separate public repo for external contribution while keeping the internal repo private, so that the contribute-to link will direct users to the public repo. Default is empty which means using the URL of current Git repo.<br><br>Example: `"git_repository_url_open_to_public_contributors": "https://github.com/Microsoft/openpublishing-docs"` | [Yes](edit-repo-properties.md) |
| git_repository_branch_open_to_public_contributors | It is used to generate content Git URL (contribute-to link) in published page. If [open_to_public_contributors](#publish-config-docsets_to_publish.open_to_public_contributors) is set to true for any docset in the repo, this config needs to be defined. If it's not defined, the generated link would contain the branch name which the content is published from, which means live for customer facing sites. Note that in order to have this field take effect, the url parameter above must be defined explicitly.<br><br>Example: `"git_repository_branch_open_to_public_contributors": "master"` | [Yes](edit-repo-properties.md) |
| <a name="need-generate-pdf-url-template"></a>need_generate_pdf_url_template | This option is to control whether to generate download PDF link in the published page. This works only in Docs site. <ul><li>`True`: if you want to show a "Download PDF" link in the published site. See [View PDF output](publish.md#service-built-pdf).</li><li>`False`: if you don't want to show the link. </li></ul><br><br>Example: `"need_generate_pdf_url_template": true` | [Yes, for live branch only](edit-repo-properties.md), automatically when setting `branch_target_mapping` |
| <a name="continue_with_document_error"></a>continue_with_document_error | This option is to control whether to continue to build the files left with document error. <ul><li>`true`: If you want to continue to build the files left with document error. </li><li>`false`: If you don't want to continue to build the files left with document error. (default value), or not defined. </li></ul><br><br>Example: `"continue_with_document_error": true` | No |
| <a name="log_codes_to_ignore"></a>log_codes_to_ignore | This option is to control whether to show broken bookmarks in your content or not. If option is not present, it will not show the broken bookmarks.<br><br>Example: `"log_codes_to_ignore": []` | No |
| <a name="resolve_user_profile_using_github"></a>resolve_user_profile_using_github | This option is to control whether to resolve user profile using GitHub. Applicable to VSO repos only. The default value is `False`.<br><br>Example: `"resolve_user_profile_using_github": True` | No |

### Configs that take effect in `live` branch only

> [!div class="mx-tdBreakAll"]
| Key | Description & Example | Available in OPS portal? |
| --- | --------------------- | ------------------------ |
| [need_preview_pull_request](preview_pull_request.md) | See the linked document for details.<br><br>Example: `"need_preview_pull_request": true` | [Yes](edit-repo-properties.md) |
| <a name="need_pr_comments"></a>need_pr_comments | The value can be `True` or `False`. <ul><li>`True` (default value), or not defined: if you want to show PR comments.</li><li>`False`: if you don't want to show PR comments. </li></ul><br><br>Example: `"need_pr_comments": false` | No |
| <a name="branch-target-mapping"></a>branch_target_mapping | You can control which branches to publish, generate PDF or generate IntelliSense from. By default, publish is enabled for all branches, while PDF/IntelliSense is not enabled.<br><br>Example:<br>`"branch_target_mapping":{ "live": [], "master":[ "Publish", "Pdf", "IntelliSense" ]}` | [Yes](edit-repo-properties.md) |
| <a name="publish-config-enable_push_aggregation"></a>enable_push_aggregation | <ul><li>`True`: if you want to aggregate pushes of same branch for each docset in the repo.</li><li>`False` (default value): if you don't want to aggregate push. </li></ul><br><br>Example: `"enable_push_aggregation": true` | No |
| <a name="publish-config-enable_pull_request_aggregation"></a>enable_pull_request_aggregation | <ul><li>`True`: if you want to aggregate pull requests of same source branch for each docset in the repo.</li><li>`False` (default value): if you don't want to aggregate pull request. </li></ul><br><br>Example: `"enable_pull_request_aggregation": true` | No |
| <a name="publish-config-enable_incremental_build"></a>enable_incremental_build | <ul><li>`True` (default value): if you want to enable incremental build for branch publishing and PR. Currently, OPS support incremental build for conceptual and managed reference documents. Enabling incremental build would normally reduce build time. It is recommenddedto enable it unless there is issue resulting in incorrect build output when turning it on.</li><li>`False` (default value): if you do not want to enable incremental build. </li></ul><br><br>Example: `"enable_incremental_build": false` | No |
| <a name="publish-config-enable_pull_request_incremental_build"></a>enable_pull_request_incremental_build | <ul><li>`True`: if you want to enable incremental build for PR. The item overwrites the value from `enable_incremental_build` for PR.<br><br>Example: `"enable_pull_request_incremental_build": false` | No |

### Deprecated but still supported configs
As OPS evolves, there are some configs that are no longer valid. However, for compatibility we still support them in case any repo still has them.

| Key | Description & Example | Available in OPS portal? |
| --- | --------------------- | ------------------------ |
| <a name="publish-config-docsets_to_publish.branches_to_filter"></a>branches_to_filter  | You can exclude any branches from publishing. OPS reads the setting from `live` branch only.<br><br>Example: `"branches_to_filter": [ "live" ]` | No |
| <a name="publish-config-need_generate_pdf"></a>need_generate_pdf | The value can be `True` or `False`. Default value is `False`. Only support build_entry_point `op` for now.<ul><li>`True`: if you want to generate pdf for each docset in the repo. You can get the generated pdf file from [portal](publish.md#service-built-pdf) </a> or [local](local-build-and-preview.md#local-pdf).</li><li>`False`: if you don't want to generate pdf. </li></ul>  OPS reads the setting from `live` branch only.<br><br>Example: `"need_generate_pdf": true` | No |
| <a name="publish-config-need_generate_intellisense"></a>need_generate_intellisense | <ul><li>`True`: if you want to generate IntelliSense for each docset in the repo. You can get the generated IntelliSense file from [portal](publish.md#service-built-intellisense) </a> or [local](local-build-and-preview.md#local-intellisense).</li><li>`False` (default value): if you don't want to generate IntelliSense. </li></ul>  OPS reads the setting from `live` branch only.<br><br>Example: `"need_generate_intellisense": true` | No |

## <a id="enablecontributions"> </a>How to enable public contributions
### If you only have one repo:
* Make the GitHub repo public in GitHub interface
* Go to [OPS portal](https://OPS), go to the docset settings and add your locale under **Public contributors** box. Click **Save**.

> [!IMPORTANT]
> You will need to be admin on the repo(s) you are trying to enable public contributions.


### If you have a private and public repo
Publishing is done from the private repo and contributions are in the public GitHub repo. These settings need to be done in the `private` repo.
* In [OPS portal](edit-repo-properties.md), go to your repo. 
* Add the public repo URL and branch you would like your customers to contribute.
* Go to the docset settings and add your locale under **Public contributors** box. Click **Save**.

> [!IMPORTANT]
> You will need to be admin on the repo(s) you are trying to enable public contributions.

This means that all your contributions coming from either review.docs.microsoft.com or docs.microsoft.com will go to the public repo. If you want your internal contributors to go to your private repo, then you will need to update the `.openpublishing.publish.config.json` file in master branch to 
* "git_repository_url_open_to_public_contributors": ""
* "git_repository_branch_open_to_public_contributors": ""

See [Syncing between repos](syncing-repos.md) to see how to sync up between repos. 

### If you want to specify different setting for specific topics
Add `open_to_public_contributors: true/false` in YAML header of individual topics.

## <a name="enable-pdf"></a>How to Enable PDF Generation

To enable PDF generation in live branch and get all the information in the config file:

1. In the [OPS portal](https://OPS), switch to **Repo view mode** from the left navigation.
2. Find your repo and select it. 
3. Click on `Settings` tab.
4. Enable `Generate PDF for live branch`.
5. Click on `Save` button.
6. In the repo, Edit docfx.json file to exclude themes.pdf for building in content. ex:
```
"content": [
      {
        "files": [
          "**/*.md", "**/*.yml"
        ],
        "exclude": [
          "**/obj/**",
          "**/includes/**",
           "**/_themes/**",
          "**/_themes.pdf/**",
          "README.md",
          "LICENSE",
          "LICENSE-CODE",
          "ThirdPartyNotices"
        ]
      }
 ```
7. Edit `.openpublishing.publish.config.json` file, and make sure you have the following entries. If not, add them:

```
"need_generate_pdf_url_template": true
```

Under `"dependent_repositories"`
```  
  {
    "path_to_root": "_themes.pdf",
    "url": "https://github.com/Microsoft/templates.docs.msft.pdf",
    "branch": "master"
  }
```
 
```
  "Targets": {  
    "Pdf": {  
    "template_folder": "_themes.pdf"  
    }  
   }, 
```

```
 "branch_target_mapping": 
  { 
    "live": ["Publish", "Pdf"]
  },
```

If you want to enable PDF generation in another branch, add PDF and Publish for your branch, after "live" branch. For example, for "master" branch:

```
  "branch_target_mapping": 
  { 
    "live": ["Publish", "Pdf"], 
    "master": ["Publish", "Pdf"]
  },
```
8. Commit and push the new configuration.

> [!NOTE] 
> After the feature is enabled, it can take some time, anywhere from a couple of minutes to a couple of hours, depending on the size of the docset, to build the PDF.
> The PDF is generated per-TOC. 

## PDF Download Dashboard
If you are curious of how many people have downloaded your PDFs, you can check the [SkyEye PDF Dashboard](https://msit.powerbi.com/groups/me/dashboards/91bb4b60-d7b2-42d6-b815-d0c566528a71/qna?q=PDF%20Download%20)
