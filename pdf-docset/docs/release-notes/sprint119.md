***Microsoft Confidential***

# APEX Sprint 119 Summary Report

Sprint dates:  05/29/2017 - 06/16/2017

Deployment date:  06/19/2017

![](media/PurpleBar.png)
## Executive Summary

Welcome to our 5th expanded summary. Thanks to everyone who has provided feedback, we are making some readability changes that hopefully will simplify the consumption of all of the information. Specifically, we have:
- Reduced the number of unique sections to make it less busy
- Provided a simple explanation of what is in each section
- Grouped updates (current and upcoming) within each section to keep in context
- Organized feature updates by scenarios to provide more context
- Switched from tables to lists for a more lightweight look
- Provided a direct feedback channel

The "big rocks" for S119 were tied to our [support for reference languages](#support-all-programming-languages-and-samples) as well as continued investments in our [localization workflow improvements](#loc-enablement).  Looking ahead to S120, we will put increased emphasis on our [Getting Started and Article Experience](#article-and-getting-started-experience-1) along with even [more localization workflow improvements](#loc-enablement-1).  The team is in the midst of our FY18/Q1 planning as well, which will see heavy investments in engineering excellence.  *More to come on that next summary*. 

ADDENDUM:  Some of the Upcoming Features that are currently planned for the next sprint will require more than one Sprint to complete.  To ensure there is no ambiguity for when those features will be delivered, the summary items will be updated to identify the targeted Sprint for release.  Those updates will be reflected in the online version of this doc.
  
> [!TIP]
> Link to Sprint 120 planning summary is [HERE](https://microsoft.sharepoint.com/teams/CE_CSI/Shared%20Documents/Sprint%20Planning/FY17Q4Planning/APEX/FY17Q4Planning-S120Review.xlsx?web=1). This list is provisional and will be updated once all the engineering teams have completed their pick-ups. VSTS query for S120 candidate features is [HERE](https://mseng.visualstudio.com/DefaultCollection/CSI/docs%20Authoring%20Experiences/_workitems?id=1bb2d2b3-0e21-494b-9796-a3b814635d92&_a=query).

![](media/BlueBar.png)
## Content Summary

This section lists new content releases on our online properties (primarily docs.microsoft.com), the release date, and the content team and PM contacts.  The localized versions of the material are also included when appropriate.

### Released this Sprint

- [Microsoft.Azure.Management.Search 1.0.2](https://docs.microsoft.com/en-us/dotnet/api/microsoft.azure.management.search?view=azuremgmtsearch-1.0.2) - 05/30/2017 - Sanketh Arvapally and Den Delimarschi
- [Microsoft.Azure.Search 3.0.4](https://docs.microsoft.com/en-us/dotnet/api/microsoft.azure.search?view=azuresearch-3.0.4) - 05/30/2017 - Sanketh Arvapally and Den Delimarschi
- [Microsoft.Azure.Search 4.0.1-preview](https://docs.microsoft.com/en-us/dotnet/api/microsoft.azure.search?view=azuresearch-4.0.1-preview) - 05/30/2017 - Sanketh Arvapally and Den Delimarschi
- [Windows Hardware](https://docs.microsoft.com/en-us/windows-hardware/get-started/) -  06/01/2017 - Paulina Cortes and Joshua Baxter
- [Batch File conventions Client Library](https://docs.microsoft.com/en-us/dotnet/api/microsoft.azure.batch.conventions.files?view=azure-dotnet) - 06/12/2017 - Sanketh Arvapally and Den Delimarschi
- [Mooncake - LOC, pre-public launch](https://docs.azure.cn/zh-cn/) - 6/12/2017 - Hui Xie, Ruixue Zhang
- [Mooncake - ENU, pre-public launch](https://docs.azure.cn/en-us/mysql/mysql-database-get-started) - 6/12/2017 - Hui Xie, Ruixue Zhang
- [VBA (MSDN) - ENU](https://msdn.microsoft.com/en-us/vba/office-vba-reference) (Office) - 6/13/207 - Sandra Aldana, John Austin

### Upcoming Sprint 120 Content Releases

- [Mooncake official launch](https://docs.azure.cn) - 6/19/2017 - Hui Xie, Ruixue Zhang
- [Dataplane services for Azure .NET and Java (Storage, SQL, Cosmos DB, Postgres, MySql, KeyVault)](https://mseng.visualstudio.com/CSI/CSI%20Team/_workItems?id=9cca58e9-ce15-4491-8960-ad9ff5deea02&_a=query) (Azure) - 6/21/2017 - Sanketh Arvapally, Den Delimarschi
- [Dynmamics Customer Engagement (Gamification)](https://mseng.visualstudio.com/CSI/_workitems/edit/981291) (Dynamics)- 6/22/2017
- [Windows Xbox .NET](https://mseng.visualstudio.com/CSI/Onboarding/_queries?_a=edit&id=1012725&triage=true) (Windows) - 6/30/2017 - Paulina Cortes & Den Delimarschi
- [Outlook MSDN - LOC](https://mseng.visualstudio.com/CSI/_workitems/edit/964553) (Office) - ~6/30/2017 - Sandra Aldana, Soran M.



![](media/RedBar.png)
## International Product Summary

This section lists the international product releases, the number of languages (in parenthesis), the release date, and the PM contact.

### Released this Sprint

- Azure Management Certificates GA	(17) - 5/31/2017 - Lynne Dong
- Intune on Azure (Admin Console) GA  (17) - 6/1/2017 -	Haiou Huangfu
- Azure Hybrid File System Public Preview (17) - 6/12/2017 - Daniel Campos
- Power BI Reporting Services RTM (10) - 6/12/2017 - Mona Nasr


### Upcoming International Product Releases

- Stream GA (43) - 6/20/2017 - Khoi Pham
- Python Tools for Visual Studio 15.3 RTW (13) - 6/26/2017 - Evelyn Kim
- Team Foundation Server 2017 Update 2 RC2 (9) - 6/26/2017 - Praveen Ganapathi Subramanian
- Advanced Threat Analytics (1.8 Client) GA (4) - 6/27/2017 - Chris Niccoli
- Azure Container Service Public Preview (17) - 6/28/2017 - Daniel Campos
- Azure Active Directory Domain Services GA (17) - 6/29/2017 - Bruno Lewin
- Azure Active Directory B2C International (Multilingual Support) GA (38) - 6/29/2017 - Bruno Lewin
- Azure Mobile App Preview (17) - 6/30/2017 - Jian Zhang
- Azure Information Protection (Windows Client Update) GA (43) - 6/30/2017 - Chris Niccoli
- Azure Health Public Preview (17) - 6/30/2017 - Daniel Campos
- System Center Configuration Manager 1706 (21) - 6/30/2017 - Haiou Huangfu
- SQL Server 2012 Service Pack 4 RTM - (10) - 7/11/2017 - Mona Nasr



![](media/OrangeBar.png)
## Features Released this Sprint

The following sections list recently shipped features by "Scenario" - that is, by the core APEX "big rock" priority. Each feature links to a feature detail section and includes the VSTS information and the PM/dev contacts.

>![](media/writer-impact.png) = Writer impact - writers, click through to the details section below!

<!-- list key shipped features by scenario - add writer impact icon if appropriate 
![](media/writer-impact.png)
-->

#### Article and Getting Started Experience

- [Configure service account for PR and Build validation in OPS Portal](#configure-service-account-for-pr-and-build-validation-in-ops-portal) ([966297](https://mseng.visualstudio.com/CSI/_workitems?id=966297&_a=edit&triage=false)) (Sandra Aldana, Jason Zhu, Feng Xu)
  

#### Support All Programming Languages and Samples

- [Base URL Path Sharing](#base-url-path-sharing) ([974119](https://mseng.visualstudio.com/DefaultCollection/CSI/_workitems?id=974119&_a=edit)) - Enable multi-repository docsets that share base URLs, resulting in faster build times and better isolation. (Brady Gaster, Zhiliang Xu, Jerry Song, Feng Xu, Yu Chen)
- [Azure SDK for Node.js Reference](#azure-sdk-for-nodejs-reference) ([711914](https://mseng.visualstudio.com/CSI/_workitems?id=711914&_a=edit)) - Onboarded the Node.js SDK for Azure to increase the language count of our reference material to include Node.js. (Brady Gaster, Simon Wu, Yannan Wang, Renze Yu, Adam Kinney)
- [Support Azure Python SDK Reference Documentation](#support-azure-python-sdk-reference-documentation) ([704506](https://mseng.visualstudio.com/CSI/_workitems?fullScreen=true&id=704506&_a=edit)) - Onboarded the Python SDK for Azure to increase the language count of our reference material to include Python. (Yun Lu, Qianhao Dong, Jinheng Wang, Adam Kinney, Yannan Wang)
- [Cognitive Toolkit (CNTK) Python API Documentation](#support-cntk-python-api-reference-documentation) ([953165](https://mseng.visualstudio.com/CSI/_workitems/edit/953165)) - Bring the Python-based SDK for Cognitive Toolkit to docs, consisting of numerous reference materials and conceptual content. (Yun Lu & Sanketh Arvapally, Jinheng Wang, Adam Kinney, Renze Yu, Yannan Wang)
- Eliminate Azure powershell processing repo ([1003194](https://mseng.visualstudio.com/CSI/_queries?_a=edit&id=1003194&triage=true)) - This feature enables content repo to directly be the processing repo eliminating a need for separate processing repo. With this feature completed along with base path sharing feature we would be in a good position to onboard any powershell on docs in a monikerized manner. (Sanketh Arvapally, Qinen Zhu)

#### Improved Content Discovery

*Nothing signficant this sprint*

#### Writer and Community Contributions

- ![](media/writer-impact.png)[Gauntlet PRMerger](#gauntlet-prmerger) ([953607](https://mseng.visualstudio.com/CSI/docs%20Authoring%20Experiences/_workitems?id=953607&_a=edit&triage=true)) - Production rollout of PRMerger2 for the **sql-docs-pr** repo (Martin O'Flaherty, Davanand Bahall)

#### Loc Enablement

- [Validate YML header before creating xliff for loc handoff](#validate-yml-header-before-loc-handoff) ([985621](https://mseng.visualstudio.com/CSI/_workItems/index?id=985621&_a=edit&triage=true)) - blocks handoff of files with yml formatting issues (SonjaS, Qin Mu)
- [Do not delete localized art referenced by localized files](#do-not-delete-localized-art-referenced-by-localized-files) ([950832](https://mseng.visualstudio.com/CSI/_workItems/index?id=950832&_a=edit&triage=true)) - prevents OpenLoc from deleting loc art still referenced by loc content files (even though equivalent en-US art has been deleted) (SonjaS, Osmond Jiang)
- [MREF and Intellisense localization enablement](#mref-and-intellisense-localization-enablement) ([1003399](https://mseng.visualstudio.com/CSI/_workItems/index?id=1003399&_a=edit&triage=true)) - enables major parts of end-to-end mref localization workflow (SonjaS, Qin Mu, Tianqi Zhang, Xuan Zhou)

#### Improved Experimentation, Feedback & Analysis

- Set word_count as metadata for conceptual documents ([1007391](https://mseng.visualstudio.com/CSI/_workitems/edit/1007391)) (Rob Eisenberg, Junkui Chen)

#### Engineering Excellence

- Increase incremental percentage when static template is updated ([984448](https://mseng.visualstudio.com/CSI/_workitems/edit/984448)) - Previously when there is an update in static template (ContentTemplate folder in template repo), a full build is needed. In this sprint, we make the build to be as incremental as possible in this scenario. (Xuan Zhou)
- Any code bug should not cause the whole docs.microsoft.com down ([1011493](https://mseng.visualstudio.com/CSI/_workitems/edit/1011493) - To avoid Docs site LSI's such [1011476](https://mseng.visualstudio.com/VSChina/_workitems/edit/1011476), we've improved the deployment steps, process and alerts so that there is unlikely a bug that can bring the whole site down from now on (Jerry Song, Qianhao Dong)
- (Split repo) publish xrefmap.yml to working repo ([998755](https://mseng.visualstudio.com/CSI/_workitems?id=998755&_a=edit)) - Loc repo need the xref mapping file pushing to fallback repo automatically. This user story enabled the automation process. This plugin also help to enable reference loc repo onboarding for yml source pushing to loc source repo after build succeed.  (Tianqi Zhang)
- Token.json files are generated from template localization pipeline ([966470](https://mseng.visualstudio.com/CSI/_workitems/edit/966470)) - enables inline keywords inserted as part of build to be localized into all 65 supported languages instead of just 17, and for translation of these keywords to be done as part of CEO pipeline instead of manually. (JeDanyow)

#### Business Continuity

*Nothing significant this sprint*

![](media/OrangeBar.png)
## Upcoming Features

The following sections list upcoming features by "Scenario" - that is, by the core APEX "big rock" priority. Each feature links to a feature detail section and includes the VSTS information and the PM/dev contacts.  Features that take more than one Sprint to complete will have the delivery Sprint identified.

<!-- list key shipped features by scenario - add writer impact icon if appropriate
![](media/writer-impact.png)
-->

#### Article and Getting Started Experience

- [Cloud Shell PowerShell Support](#cloud-shell-powershell-support) ([656324](https://mseng.visualstudio.com/CSI/_workitems?id=656324&_a=edit)) - Enhancing Azure PowerShell samples to have the same "Try It" Cloud Console functionality that the Bash samples do today. (Rob Eisenberg)
- ![](media/writer-impact.png)[Tabbed Conceptual](#tabbed-conceptual) ([710460](https://mseng.visualstudio.com/CSI/_workitems?id=710460&_a=edit)) - Enabling tabbed content within Markdown articles. (Rob Eisenberg)
- [Markdown Standardization and Extensibility](#markdown-standardization-and-extensibility) ([923144](https://mseng.visualstudio.com/CSI/_workitems?id=923144&_a=edit)) - Aligning our Markdown parser to GFM CommonMark compatible syntax while providing a Markdown extensibility model. (Rob Eisenberg)
- ![](media/writer-impact.png)[Interactive .NET code REPL](#interactive-net-code-repl) ([656325](https://mseng.visualstudio.com/CSI/_workitems?id=656325&_a=edit)) - Enhancing C# samples to have a similar experience to "Try It" for Cloud Shell. (Rob Eisenberg)
- ![](media/writer-impact.png)[Interactive Tutorials](#interactive-tutorials) ([795312](https://mseng.visualstudio.com/CSI/_workitems?id=795312&_a=edit)) - Step-by-step, stateful, tutorial experiences that incorporate interactive components such as the Cloud Shell and .NET REPL. (Rob Eisenberg)
- ![](media/writer-impact.png)[Preserve Article Context](#preserve-article-context) ([931391](https://mseng.visualstudio.com/CSI/_workitems?id=931391&_a=edit)) - The next generation of Contextual ToC and Breadcrumbs, designed to clean up docs URLs and be a more extensible mechanism for the future. (Rob Eisenberg)
- [Yaml Document Processor Enhancements](#yaml-document-processor-enhancements) ([983782](https://mseng.visualstudio.com/CSI/_workitems?id=983782&_a=edit)) - Enabling full-fidelty, data-driven content generation via Yaml. (Rob Eisenberg)
- [New 404 Page](#new-404-page) ([891858](https://mseng.visualstudio.com/CSI/_workitems?id=891858&_a=edit)) - A stylish, fun and helpful new 404 page for docs. (Rob Eisenberg)


#### Support All Programming Languages and Samples

- [Enhanced Code Samples](#enhanced-code-samples) ([953670](https://mseng.visualstudio.com/CSI/_workitems?id=953670&_a=edit)) - Moving the code sample language selector to be inline with the sample, allowing sample GitHub links and adding new language colorization. (Rob Eisenberg)

#### Improved Content Discovery 

- ![](media/writer-impact.png)[Conceptual Versioning](#conceptual-versioning) ([953675](https://mseng.visualstudio.com/CSI/_workitems?id=953675&_a=edit)) - Enabling versioning of conceptual content in conjunction with product release changes. (Rob Eisenberg)

#### Writer and Community Contributions

- ![](media/writer-impact.png)[Gauntlet Version 2](#gauntlet-version-2) (Megan Bradley/Martin O'Flaherty)

#### Loc Enablement

- [Force Publishing for IntelliSense](#force-publishing-for-intellisense) ([1012899](https://mseng.visualstudio.com/CSI/_workItems/index?id=1012899&_a=edit&triage=true) - allows user to force-publish Intellisense from OPS portal (SonjaS, Jason Zhu, Sandra Aldana)
- [Single file publishing for localized content](#single-file-publishing-for-localized-content) ([769889](https://mseng.visualstudio.com/CSI/_workItems/index?id=769889&_a=edit&triage=true) - one file with error will no longer block the whole handback batch from publishing (SonjaS)
- [Push MREF Host File Tag to iCMS](#push-host-file-tag-to-icms) ([1009747](https://mseng.visualstudio.com/CSI/_workItems/index?id=1009747&_a=edit&triage=true) - OpenLoc will push metadata denoting a file as MREF to iCMS (SonjaS)
- [Improved error handling from iCMS](#improved-error-handling-from-icms) ([799282](https://mseng.visualstudio.com/CSI/_workItems/index?id=799282&_a=edit&triage=true) - improve user experience by providing error messages (SonjaS)
- [Enable MREF localization in iCMS](#enable-mref-localization-in-icms) ([866409](https://mseng.visualstudio.com/CSI/_workItems/index?id=866409&_a=edit&triage=true) - enables handoffs/handbacks of OpenLoc mref files via iCMS (SonjaS)


#### Improved Experimentation, Feedback & Analysis

- [Move to JSLL for Telemetry](#move-to-jsll-for-telemetry) ([967657](https://mseng.visualstudio.com/CSI/_workitems?id=967657&_a=edit)) - Migrating our current site telemetry implementation from WEDCS to JSLL. (Rob Eisenberg)

#### Engineering Excellence

*Nothing significant next sprint*

#### Business Continuity 

*Nothing significant next sprint*

![](media/GreenBar.png)
## Feature Details

<!-- 
Provide details in H2 sections below. Describe features, explain impact, and link to user docs, etc. Use screen shots to show what's cool! List items in the same order as the summary tables above.
-->



### Configure Service Account for PR and Build Validation in OPS Portal

Users can now configure their repos in OPS Portal to have service accounts for PR and build validation instead of the account of an employee. When the user account does not have enough permissions, it would default back to the user who provisioned the repo. If that user is no longer valid or the user does not have the right permissions, OPS build will return a warning or an error to the user. (Sandra Aldana, Jason Zhu, Feng Xu)

***

### Base URL Path Sharing

Make changes to the hosting layer and to OPS so that it they support having one base URL path that is served from +1 repositories. This would give us the ability to have SQL PowerShell in one repo, Azure PowerShell in another repo, but to have URLs such as those below which would result with users having a consistent base URL for all the PowerShell module references. 

In the example URLs below, the bold segment is the segment we want to be consistent. 

> DMC/powershell/module/sqlps/add-sqlavailabilitygrouplistenerstaticip
DMC/powershell/module/azurerm.resources/get-azurermadgroup

The "module/{moduleName}/{cmdletName}" URL segments are specific to PowerShell, but this is a feature that will be useful to numerous reference docsets and product groups.

***

### Azure SDK for Node.js Reference

Support the OpenDev event in June with a new Node.js reference site for the Azure Node.js SDK. This feature adds another language to the list of references supported by docs, it also delivers on the mission of unifying our Azure SDK contents in a single site rather than force customers to use multiple sites. 

> Brady to add screen shot

***

### Support Azure Python SDK Reference Documentation

Currently, Azure Python SDK reference docs of management libraries are on [ReadtheDocs](http://azure-sdk-for-python.readthedocs.io/en/latest/) built with Sphinx using themes provided by Read the Docs. We will migrate these reference content to https://docs.microsoft.com for OpenDev Event. We use the Sphinx-DocFX-YAML converter and the Python DocFX processor to support autogenerating Azure Python SDK reference documentation. 

***

### Support CNTK Python API reference documentation

Before we onboard CNTK Python API reference documentation to docs.microsoft.com, no Python API documentation was hosted on docs.microsoft.com. DocFX reference materials didn't support generating Python API documentation. CNTK python API reference docs was on https://cntk.ai/pythondocs/apireference.html built with Sphinx using a theme provided by Read the Docs. On May 31, we migrated the CNTK Python API reference documentation on https://cntk.ai/pythondocs/apireference.html to https://docs.microsoft.com/en-us/python/cognitive-toolkit/?view=cntk-py-2.0.       
To support generating Python API reference documentation on docs.microsoft.com,        
* Eric Holscher from Read the Docs built a Sphinx-DocFX-YAML converter which can convert python API to DocFX readable YML files. DocFX will consume these YML files to generate yml files for OPS.    
* We built a new DocFX processor for python. Actually this processor can support Python, JavaScript, C# and so on. It can save us a lot of effort on creating new processors and template for new ref languages. 
* We built a new template for python. 

***

### Gauntlet PRMerger
PRMerger has been rewritten as a Gauntlet component, PRMerger provides automated pull request review and merging if certain criteria are met, has been integrated into Gauntlet running live on the **sql-docs-pr** repo now. Also onboarded to this repo this sprint was the PR review team and Acrolinx. PRMerger will be rolled out all of the other repos over the coming sprints with *azure-docs-pr* next on the list.

**More info**<br>
[http://aka.ms/prmergeroverview](http://aka.ms/prmergeroverview)


***


### Validate yml header before loc handoff

Prevents handoff of files for localization which can be localized, but then cannot be transformed back from xliff to md because the yaml header has formatting problems. The handoff transform will throw an error if the yaml header of the markdown file does not contain quotes around following characters:  :, {, }, [, ], ,, &, *, #, ?, |, -, <, >, =, !, %, @, `.
Feature is implemented for standalone OpenLoc as well as iCMS-integrated OpenLoc.

***

### Do not delete localized art referenced by localized files

One of the great features of OpenLoc is that it keeps localized repos in sync with en-US repos (if an en-US file is deleted, the equivalent loc files are deleted). While this is generally a great feature, there is a problem when localized content has a time lag, and the to-be-published loc version is still referencing a localized art that is now deleted (because the en-US art was deleted). This feature ensures OpenLoc scans the loc files for any references to art pieces before deleting any art pieces from loc repos.  This feature has already been in production in standalone OpenLoc, but has now also been enabled in iCMS-integrated OpenLoc.

***

### MREF and IntelliSense localization enablement

Mostly finishing in sprint119 (additional items following in s120), this enables large parts of the end-to-end loc workflow for mref and intellisense. During build, yaml files are dropped to a special YAML4Loc repo, where they will be transformed with a special mref-yaml transform to the localizable xliff file format, and placed into the handoff repo. The xliff transformer will auto-recognize that the mref yamls are different from e.g. TOC.yaml files. 


***

<!-- coming soon feature details start here -->

### Cloud Shell PowerShell Support

We're working on the ability to enable Azure PowerShell code samples to be run directly from within docs.microsoft.com. Code samples for which this is enabled will have a "Try It" button. Clicking that button will display the Azure Cloud Shell in PowerShell mode at the bottom of the screen. This work is being done as part of a cross-org collaboration with the Azure Cloud Shell team.

**More info**<br>

  - Release Timing - We hope to finish the initial implementation during S120. We will need additional sprints leading up until the September launch of the PowerShell Cloud Shell to stay synced with the team that is delivering the Azure Portal experience.
  - [The Enhanced Code Samples Spec](https://review.docs.microsoft.com/en-us/new-hope/specs/markdown/enhanced-code-samples?branch=master)

***

### Tabbed Conceptual

Today we have to duplicate large sets of content and fragment our content story because there's no way to represent an article such as "Create a Virtual Machine" without providing multiple articles, one on Bash, one on PowerShell and one on Azure Portal. Similar problems exist for other partners that need to pivot around other factors such as Desktop, Mobile or Web. This feature enables conceptual content that is multi-faceted, such that various sections of a document can contain multiple renderings, each covering the same core concept or task but allowing for customer preferences in tooling, platform, language, etc. to decide what is displayed for reading.

**More info**<br>

  - Release Timing - We expect to have an implementation ready for writer experimentation during the S120 sprint. Assuming no unexpected issues, we should be able to ship this at the end of S120.
  - [The Tabbed Conceptual Spec](https://review.docs.microsoft.com/en-us/new-hope/specs/conceptual/tabbed-conceptual?branch=master)

***
### Markdown Standardization and Extensibility

The current features of our Markdown parser aren't robust enough to support the needs of building future Markdown extensions that are consistent, scalable, standard, safe and performant. This work re-aligns our Markdown parser by building on top of open source, standardizing on GFM CommonMark syntax/semantics, improving performance and lowering memory usage. The new parser will also enable easier creation of extensions to the Markdown language so that we can more efficiently evolve our conceptual content vocabularly on docs.

**More info**<br>

  - Release Timing: This is an ongoing effort to improve our core Markdown story. We don't yet have a target release date. This is expected to continue throughout FY18Q1.
  - [The Markdown Standardization and Extensibility Spec](https://review.docs.microsoft.com/en-us/new-hope/specs/markdown/markdown-extensibility?branch=master)

***
### Interactive .NET code REPL

We're working on the ability to enable C# code samples to be run directly from within docs.microsoft.com. Code samples for which this is enabled will have a "Try It" or "Run It" button. Clicking that button will transform the code sample into a live Monoco editor and run the code using the new .NET REPL service. This work is being done as part of a cross-org collaboration with the .NET team.

**More info**<br>

  - Release Timing - The final release of this feature relates to the .NET team's planned browser experience launch. We are working closely with the .NET team to co-evolve the Docs and .NET experience. We believe we will have a version of this feature available in review during S120. Work will likely continue for additional sprints as we sync and plan for the .NET launch.
  - [The Interactive .NET code REPL Spec](https://microsoft.sharepoint.com/teams/CE_CSI/Shared%20Documents/Forms/AllItems.aspx?id=%2Fteams%2FCE%5FCSI%2FShared%20Documents%2FCSI%20Spec%20Library%2FDocs%2FDotNet%2DInteractive%2DRepl%2Edocx&parent=%2Fteams%2FCE%5FCSI%2FShared%20Documents%2FCSI%20Spec%20Library%2FDocs&p=true)

***
### Interactive Tutorials

Today on docs we have only two types of content: reference and conceptual. Reference content isn't geared towards those who are getting started. Conceptual content can meet this need. However, to accomplish a step-by-step process with today's technology, one must construct special sub ToCs resulting in a non-fluid experience that lacks any persistent state tracking or rich interaction. The end result is a degraded getting started experience for the customer.

Interactive Tutorials are a new form of conceptual content that build on our existing foundation. A Tutorial takes a customer through an interactive, step-by-step experience. It features a custom landing page, rich with contextual information related to the Tutorial, an in-page step-by-step process, persistent progress tracking, interactive code editors, CLIs...and more.

**More info**<br>

  - Release Timing - Engineering work started during S119 and will continue into S120. We hope to have a version of this feature in review by the end of S120. We'd like to take S121 to allow writers to create some content in review and work with us to polish the feature for launch at the end of S121.
  - [The Interactive Tutorials Spec](https://review.docs.microsoft.com/en-us/new-hope/specs/conceptual/interactive-guides?branch=master)

***

### Preserve Article Context

Today, when a customer is on a documentation page with a UHF custom L1 and they perform a search, the search results page does not display the same UHF L1 branding, but falls back to the default docs L1. Likewise, if an article is being displayed in association with a Contextual ToC, then the article's associated UHF L1 is displayed rather than the one associated with the ToC. This causes a brand switch, mid-content. Neither of these scenarios provides the type of consistent experience that we want on docs.microsoft.com.

Additionally, the contextual ToC query string does not also enable the correct breadcrumbs to be displayed. These are handled by two separate query string values, the second of which is often forgotten by the ToC author. This proliferation of query strings presents maintenance problems for content creators. It also results in uglier URLs for customers.

Finally, when combining these contextual items with versioning, ToC creation and management complexity explodes to a degree that is not reasonable for writers.

For these and other reasons, we're making the idea of "context" something that is an explicit part of the docs architecture. Any page will be able to reference a "context" which will allow the docs platform to automatically flow in the correct header, breadcrumbs, ToC and any other contextual data or visualizations. This mechanism cleans up our URLs and provides an extensible system for the future.

**More info**<br>

  - Release Timing - This feature is strongly tied to work happening on Conceptual Versioning. This work will be done incrementally over the next 3 sprints: 120, 121, and 122.
  - [The Preserve Article Context Spec](https://review.docs.microsoft.com/en-us/new-hope/specs/site-experience/preserving-article-context?branch=master)

***

### Yaml Document Processor Enhancements

Improving the Yaml Document Processor capabilities of OPS to a higher fidelity, first-class citizen. Details include:

- Establishing a standard metadata section for all Yaml files
- Enabling URL to Git source file mapping; used by the Edit button and BI
- Linking Git contributor info
- Generating proper document ids; used by BI and commenting systems.
- Supporting Markdown content in Yaml
- Supporting external file link processing
- Supporting Yaml-localized property values
- Supporting Yaml Schemas for OPS build validation, content generation and tooling support

Some of these features have been delivered. However, the more complex features are still undergoing technical design and implementation.

**More info**<br>

  - Release Timing - The first part of this feature, fixes to missing metadata, shipped during S119. These were corrections to the original Yaml Processor rollout. As part of this process, a number of additional scenarios were discovered and an updated plan has been identified. The new Scmema-based Yaml processor will be incrementally built over the next 3 sprints: 120, 121 and 122.

***
### New 404 Page

We're working on a new 404 page for docs that provides a modern, fun experience for our customers. We're working to polish it and make a plan to ship it. Stay tuned for more information and get your gamepads ready...

**More info**<br>

  - Release Timing - There is no planned release date for this feature currently. Both design and engineering are working on this between other tasks as time allows. We are close to a final design and hope to take the engineering to the next stage during S120 and S121.

***

### Enhanced Code Samples

Customers like .NET need a way to show a code sample, allowing the customer to select which language they want to view the sample in. On top of this, there's no way currently for customers to follow the sample displayed in docs, back to the original source on Github. This feature tracks moving the code sample language selector to be inline with the sample, allowing sample GitHub links and adding new language colorization.

**More info**<br>

  - Release Timing - This is an ongoing set of work to improve our code snippets on docs. During S120 we'll be adding support for configuring the Azure PowerShell language and interactive mode as well as adding support for "vanilla" Bash. Future updates will include support for new languages, improvements to the language selector UI and performance enhancements. We hope to roll out these additional improvements incrementally over the sprints during FY18Q1.
  - [The Enhanced Code Samples Spec](https://review.docs.microsoft.com/en-us/new-hope/specs/markdown/enhanced-code-samples?branch=master)

***

### Conceptual Versioning

As product teams move through the software lifecycle, they produce new versions that either add to or change the core features and capabilities of their products. In response to these changes, a documentation platform needs to be able to display different versions of documentation corresponding with the different product releases. For technical products, this includes two parts: conceptual content and reference content. This feature covers versioning of conceptual content.

**More info**<br>

  - Release Timing - This work will be done over the next 3 sprints: 120, 121 and 122. We'll attempt to release the feature incrementally if we can, with Folder-based versioning first. This will depend on the ability to synchronize the frontend and backend teams at intermediary stages during feature development.
  - [The Conceptual Versioning Spec](https://review.docs.microsoft.com/en-us/new-hope/specs/ops/conceptual-versioning?branch=master)

***
### Gauntlet Version 2

Gauntlet version 2 is finishing UAT and releasing to production. This release includes validation, which enables content team admins to configure validation rules in the Gauntlet web UI, and writers and other contributors to validate their files via the Gauntlet VS Code extension. It also includes the ability to insert bookmark links and Channel 9 and YouTube videos.

A console application to validate a full cloned repo at once will also be available.

**More info**<br>

[Dogfood docs](http://aka.ms/GauntletDFDocs)

***



### Force publishing for intellisense

Currently Intellisense builds are generated each time an updated file is checked into the repo. We are enabling force publishing, so builds can be generated on demand and the loc team can take snapshot builds when needed. 

***

### Single file publishing for localized content

Localization often works in batch-mode - many files are handed off together, are localized, and handed back. If a handback file causes a publishing error, the whole handback batch publishing job fails. This feature is to enable users to specify which errors should block publishing on a per-file basis, not a per-batch basis.


***

### Push host file tag to icms

iCMS has rich metadata which is provided to localization suppliers. OpenLoc will now provide an MREF-specific metadata for each xliff MREF file; the localization supplier can use this metadata to know that the file is MREF and that it needs to be processed differently (typically we localize the intellisense strings with human translation quality, and the remainder of the mref strings with machine translation quality).

***

### Improved error handling from icms

The OpenLoc-iCMS integration needs better error messages and better error handling when provisioning a new project, as well as making handoffs and handbacks.


***

### Enable mref localization in icms

MREF localization is just getting enabled in the standalone OpenLoc pipe, and will now also get hooked up for the iCMS-integrated pipe.
     
***
### Move to JSLL for Telemetry

The WEDCS telemetry library is being decommissioned so docs.microsoft.com is migrating all site telemetry over to the JSLL library.

***








![](media/PurpleBar.png)
## Resources

- [OPS Yammer Group](https://www.yammer.com/microsoft.com/#/threads/inGroup?type=in_group&feedId=7133984)
- [OPS docs](https://opsdocs.azurewebsites.net/en-us/opsdocs/index?branch=master)
- [DRAFT Onboarding guides](https://review.docs.microsoft.com/en-us/help/contribute/)
- DL: Join [this group](http://idwebelements/GroupManagement.aspx?Group=ceapexsprint&Operation=join) to subscribe to this sprint summary!

## Leave (Un-subscribe)
http://idwebelements/GroupManagement.aspx?Group=ceapexsprint&Operation=leave 

## Join (Subscribe)
http://idwebelements/GroupManagement.aspx?Group=ceapexsprint&Operation=join 

## Send Feedback
[Email APEX Planning Council](mailto:hamms@microsoft.com).
