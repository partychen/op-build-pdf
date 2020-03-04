***Microsoft Confidential***
# APEX Sprint 118 Summary Report

Sprint dates:  05/08/2017 - 05/26/2017

Deployment date:  05/31/2017 (the deployment date is postponed from 05/29/2017 due to Dragon Boat Festival in China)

![exec-summary](media/exec-summary.png)

The previous Sprint was focused on ensuring all of the //Build-related features and content were in a ready-state, which helped ensure a very successful customer experience during the event itself. There have already been a number of summaries sent on that, so I will avoid repeating that here.  Sprint 118 saw several internal features aimed at our internal loc workflows, as well as the release of our authoring toolset (aka [Gauntlet](http://aka.ms/GauntletDocs)) for internal content authors.
 
In addition, this marks the first summary where we are starting to provide visibility to the International Products Released and the Upcoming International Product Releases planned for next Sprint.   We are aware that the amount of information we are sharing has grown significantly since we started, and we already have plans to iterate and improve in the upcoming sprints.
To everyone in the US, have a great long Memorial Day Weekend.

<br>

> [!TIP]
> Link to Sprint 119 planning summary is [HERE](https://microsoft.sharepoint.com/teams/CE_CSI/Shared%20Documents/Sprint%20Planning/FY17Q4Planning/APEX/FY17Q4Planning-S119Review.xlsx?web=1). This list is provisional and will be updated once all the engineering teams have completed their pick-ups. VSTS query for S119 candidate features is [HERE](https://mseng.visualstudio.com/CSI/_workitems?id=a210af14-3139-40c2-94f7-f08c7c58bef5&_a=query).

<br>

![what-shipped-content](media/what-shipped-content.png)

|Click for live URL!  |Go live date  |Contacts  |Group  |
|---------|---------|---------|---------|
| [R Tools for Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/) | 5/10/17  | Kraig Brockschmidt | Visual Studio |
|[Springfield-MSRD Dev Center](https://docs.microsoft.com/en-us/security-risk-detection)| 5/8/2017| Dave Tamasi <br> Sanketh Arvapally| MSRD Dev Center|
|[Cognitive Toolkit - Conceptual](https://review.docs.microsoft.com/en-us/cognitive-toolkit)| 5/8/2017| Dave Ahlers <br> Sanketh Arvapally| Cognitive Toolkit|
|[PowerShell 4.0](https://docs.microsoft.com/en-us/powershell/azure/overview?view=azurermps-4.0.0)| 5/10/2017|Sean Wheeler <br> Sanketh Arvapally| Azure |
|[Bot Framework .NET Reference](https://docs.microsoft.com/en-us/dotnet/api/?view=botbuilder-3.8)| 5/10/2017|Den Delimarsky <br> Sudeep Kumar| Azure |
|[HealthVault .NET Reference](https://docs.microsoft.com/en-us/dotnet/api/?view=healthvault-1.65.20508.1-preview)| 5/10/2017|Sandra Aldana Abad <br> Den Delimarsky | HealthVault |

![what-shipped-loc-prod](media/what-shipped-loc-prod.png)
| Product Name                                           | Num Languages  | Release Date  | PM            |
|--------------------------------------------------------|----------------|---------------|---------------|
| .NET Core Template Engine                              | 23             | 05/10/17      | Honghui Guo   |
| Azure Health Public Preview                            | 17             | 05/10/17      | Daniel Campos |
| Python Tools for Visual Studio 15.2 GA                 | 13             | 05/10/17      | Evelyn Kim    |
| R Tools for Visual Studio 15.2 GA                      | 13             | 05/10/17      | Evelyn Kim    |
| Visual Studio 2017 (Dev15) Update 2 RTW                | 13             | 05/10/17      | Daniel Ye     |
| Visual Studio for Mac OS GA                            | 13             | 05/10/17      | Daniel Ye     |
| Azure Active Directory Identity Access Management GA   | 17             | 05/15/17      | Kevin Liang   |
| Azure Container Registry                               | 17             | 05/19/17      | Honghui Guo   |
| System Center 2012 R2 UR13                             | 17             | 05/23/17      | Khoi Pham     |
| System Center 2016 UR3                                 | 17             | 05/23/17      | Khoi Pham     |
| Azure Stack "1705" Release                             | 17             | 05/26/17      | Bruno Lewin   |
| Team Foundation Server 2017 Update 2 RC1               | 9              | 05/26/17      | Kevin Liang   |

![what-shipped-features](media/what-shipped-features.png)

|Click for details!  |VSTS  |Owners  |Impact  |
|---------|---------|---------|---------|
|[Enable bilingual publishing for CEO](#enable-bilingual-publishing-for-ceo) |[950241](https://mseng.visualstudio.com/CSI/_workItems/index?id=950241&_a=edit&triage=true) | Qin Mu (dev), Sonja Saltzman (PM), Eman Shaheen (PM) | End users and loc PMs |
|[Aggregate AirLoc HB messages in OpenLoc to avoid HB problems](#aggregate-airloc-hb-messages-in-openloc-to-avoid-hb-problems) | [987803](https://mseng.visualstudio.com/CSI/_workItems/index?id=987803&_a=edit&triage=true) | Osmond Jiang (dev), Sonja Saltzman (PM) | Loc PM, Support Engineer,         |
|[Offline Book: Support "view online" page for not-downloaded (OPS) topic](#offline-book-support-view-online-page-for-not-downloaded-ops-topic) |[968779](https://mseng.visualstudio.com/DefaultCollection/CSI/_workitems/edit/968779) | Hui Xie (PM) <br> Jinheng Wang (Dev) | Offline book users |
|[Support CNTK Python API reference documentation](#Support-CNTK-Python-API-reference-documentation)|[953165](https://mseng.visualstudio.com/DefaultCollection/CSI/_workitems?id=953165&_a=edit)|Yun Lu (PM)<br>Zhiliang Xu/Ying Hua/Adam Kinney (Dev)<br> Sanketh Arvapally(onboarding)|Onboard CNTK Python API reference documentation|
| [AFD Integration and Audience Segmentation](https://review.docs.microsoft.com/en-us/new-hope/specs/experimentation/audience%20segmentation) | [945741](https://mseng.visualstudio.com/CSI/_workitems?id=945741)| Saurabh Choudhury (PM) <br> Ricky Kurniawan (Dev) Simon Wu (Dev) <br> Sarah Baranowski (Researcher) | Writers and PMs| 
| [Feature Experimentation](https://review.docs.microsoft.com/en-us/new-hope/specs/experimentation/feature%20experimentation) | [945744](https://mseng.visualstudio.com/CSI/_queries?_a=edit&id=945744&triage=true)| Saurabh Choudhury (PM) <br> Ricky Kurniawan (Dev) Simon Wu (Dev) <br> Sarah Baranowski (Researcher) | PMs| 
|[Emulate MVC TOC structure for partners](https://mseng.visualstudio.com/CSI/_workitems?id=965415&_a=edit)|[965415](https://mseng.visualstudio.com/CSI/_workitems?id=965415&_a=edit)|Brady Gaster, Ying Hua, Jessie Huang|REST customers and partners|
|[Finalize generalization of REST API reference](https://mseng.visualstudio.com/DefaultCollection/CSI/_workitems?id=983072&_a=edit)|[983072](https://mseng.visualstudio.com/DefaultCollection/CSI/_workitems?id=983072&_a=edit)|Brady Gaster, Ying Hua, Jessie Huang|REST customers and partners|
|[Moniker Management in OPS Portal](https://review.docs.microsoft.com/en-us/new-hope/specs/ops/moniker-management)|[968216](https://mseng.visualstudio.com/CSI/_workitems/edit/968216)|Sandra Aldana Abad, Jason Zhu, Den Delimarsky|OPS partners and onboarding PMs|
|[Gauntlet Release to Production](#gauntlet-release-to-production) |  |Megan Bradley (PM)<br>Martin O'Flaherty (PM)<br>Jonathan Duncan's team (Dev)|docs.microsoft.com contributors. |

![coming-soon-content](media/coming-soon-content.png)

|Release  |VSTS    |Owners  |Group  |
|---------|---------|---------|---------|
|[Mooncake](https://review.docs.azure.cn/zh-cn/traffic-manager/traffic-manager-configure-weighted-routing-method?branch=master) |  [966148](https://mseng.visualstudio.com/DefaultCollection/CSI/_workitems/edit/966148) | Johnny V Chen <br> Hui Xie | Azure | 
|Windows Hardware|[1006871](https://mseng.visualstudio.com/CSI/Onboarding/_queries?_a=edit&id=1006871&triage=true)|Joshua Baxter <br> Paulina Cortes | Windows|


![coming-soon-loc-prod](media/coming-soon-loc-prod.png)


|Product Name                                                         | Num Languages | Release Date  | PM               |
|---------------------------------------------------------------------|---------------|---------------|------------------|
| Azure Active Directory B2C International (Multilingual Support) GA  | 38	          | 05/30/2017	  | Bruno Lewin      |
| Azure Mobile App Preview                                            |	17	          | 05/31/2017    |	Lynne Dong       |
| Azure Management Certificates GA                                    |	17            | 05/31/2017	  | Lynne Dong       |
| Stream GA	                                                          | 43	          | 06/01/2017	  | Khoi Pham        |
| Azure Stack "1705" Release                                          |	17     	      | 06/02/2017	  | Bruno Lewin      |
| SQL Server 2012 Service Pack 4 RTM                                  |	10	          | 06/6/2017	  | Mona Nasr        |
| Azure Hybrid File System Public Preview                             |	17	          | 06/12/2017	  | Daniel Campos    |
| Power BI Reporting Services RTM                                     |	10	          | 06/12/2017	  | Mona Nasr        |
| Team Foundation Server 2017 Update 2 RC2                            |	9	          | 06/16/2017	  | Kevin Liang (CE) |
| Python Tools for Visual Studio 15.3 RTW                             |	13	          | 06/26/2017	  | Evelyn Kim       |
| Advanced Threat Analytics Client GA                                 |	4	          | 06/27/2017	  | Chris Niccoli    |
| Azure Active Directory Domain Services GA                           |	17	          | 06/29/2017	  | Bruno Lewin      |
| Azure Information Protection (Windows) GA	                          | 43	          | 06/30/2017	  | Chris Niccoli    |
| System Center Configuration Manager [1706]                          |	21	          | 06/30/2017	  | Haiou Huangfu    |
| Azure Health Public Preview                                         |	17	          | 06/30/2017    |	Daniel Campos    |
| Azure Key Vault GA	                                              | 17	          | 06/30/2017	  | Chris Niccoli    |


![coming-soon-features](media/coming-soon-features.png)

|Click for details!  |VSTS  |Owners  |Impact  |
|---------|---------|---------|---------|
|[Create loc HO xliff files from ecmaxml instead of yml](#create-loc-ho-xliff-from-ecmaxml)   | [1003401](https://mseng.visualstudio.com/CSI/_workItems/index?id=1003401&_a=edit&triage=true) | Sonja Saltzman (PM)<br>Alice Wang, Ying Hua (Dev)   | End users and loc PMs |
|[Automatically update zip files with links so loc has working links](#automatically-update-zip-file)    | [999025](https://mseng.visualstudio.com/CSI/_workItems/index?id=999025&_a=edit&triage=true) | Sonja Saltzman (PM)<br>Tianqi Zhang, Ying Hua (Dev)   | End users and loc PMs |
|[MREF and Intellisense content can be localized in CEO pipe](#mref-intellisense-in-ceo-pipe)| [866409](https://mseng.visualstudio.com/CSI/_workItems/index?id=866409&_a=edit&triage=true) |Sonja Saltzman (PM)<br>Qin Mu (Dev)  | End users and loc PMs |
|[Do not delete referenced arts in CEO pipe](#do-not-delete-referenced-arts-in-ceo-pipe) | [950832](https://mseng.visualstudio.com/CSI/_workItems/index?id=950832&_a=edit&triage=true)  | Sonja Saltzman (PM)<br>Qin Mu (Dev) | End users and loc PMs  |
|[Validate Yml header before handoff](#validate-yml-header-before-handoff) | [985621](https://mseng.visualstudio.com/CSI/_workItems/index?id=985621&_a=edit&triage=true)   |  Sonja Saltzman (PM)<br>Yufei Huang (Dev) | Loc PMs        |
|[Conceptual Versioning](#conceptual-versioning) | [953675](https://mseng.visualstudio.com/DefaultCollection/CSI/_workitems?id=953675) | Rob Eisenberg (PM) | Writers, End Users |
|[Markdown: Content Switcher](#markdown-content-switcher)| [710460](https://mseng.visualstudio.com/DefaultCollection/CSI/_workitems?id=710460) | Rob Eisenberg (PM) | Writers, End Users |
|[Interactive Tutorials](#interactive-tutorials) | [795312](https://mseng.visualstudio.com/CSI/_workitems?id=795312&_a=edit) | Rob Eisenberg (PM) | Writers, End Users |
|[Interactive C# REPL](#interactive-c-repl) | [656325](https://mseng.visualstudio.com/CSI/_workitems?id=656325&_a=edit) | Rob Eisenberg (PM) | Writers, End Users |
|[New 404 Page](#404-page) | [891858](https://mseng.visualstudio.com/CSI/_workitems?id=891858&_a=edit) | Rob Eisenberg (PM) | End Users |
|[Enable SidexSide mouse hover over experience](#enable-sidexside-mouse-hover-over-experience) |[656333](https://mseng.visualstudio.com/7fbb5c5f-3d2e-4ed3-8542-f12cafd777fe/_workitems?projectId=7fbb5c5f-3d2e-4ed3-8542-f12cafd777fe&src=WorkItemMention&src-action=artifact_link&fullScreen=true&id=656333&_a=edit)|Eman Shaheen (PM)<br>Yufei Huang (Dev)<br>Maya Stewart (PM) for content testing |End Users |
|[Enable right to left support for content](#enable-right-to-left-support-for-content) |[644222](https://mseng.visualstudio.com/DefaultCollection/VSChina/_workitems?fullScreen=false&id=644222&_a=edit)|Eman Shaheen (PM)<br>Geoff Knutzen (Dev)<br> |End Users |
|[PRMerger Gauntlet integration (dogfood)](#prmerger-gauntlet-integration) |[796423](https://mseng.visualstudio.com/CSI/_workitems?id=796423&_a=edit&triage=true)|Eman Shaheen (PM)<br>Martin O'Flaherty (PM)<br>Davanand Bahall (Dev)|Writers, other contributors |
|[Gauntlet Metadata Validation (dogfood)](#gauntlet-metadata-validation) |[658002](https://mseng.visualstudio.com/DefaultCollection/CSI/_workitems?id=658002&_a=edit&triage=true)|Sudeep Kumar (PM)<br>Megan Bradley (PM)<br>Peter Ibekwe (Dev)<br>Petr Abraham (Dev)  |Writers, BI team  |
|[Gauntlet Telemetry](#gauntlet-telemetry)|[697290](https://mseng.visualstudio.com/CSI/_workitems?id=697290&_a=edit)|Martin O'Flaherty|APEX engineering, planning|
|[Script to build master redirect file](#script-to-build-master-redirect-file)|[979806](https://mseng.visualstudio.com/CSI/_workitems?id=979806&_a=edit)|Sanketh Arvapally(PM)<br>Megan Bradley (PM)|docs.microsoft.com repo owners|
|[Improve REST API Parameter Layout](#improve-rest-api-parameter-layout)|[949745](https://mseng.visualstudio.com/DefaultCollection/CSI/_workitems?id=949745&_a=edit)|Brady Gaster, Ying Hua, Jessie Huang|REST customers and partners|
|[Support x-parameterized-host](#support-x-parameterized-host)|[928260](https://mseng.visualstudio.com/DefaultCollection/CSI/_workitems?id=928260&_a=edit)|Brady Gaster, Ying Hua, Jessie Huang|REST customers and partners|
|[Azure Node.js SDK](#azure-node.js-sdk)|[711914](https://mseng.visualstudio.com/DefaultCollection/CSI/_workitems?id=711914&_a=edit)|Brady Gaster, Ying Hua, Jessie Huang|Node.js customers and partners, the upcoming conference|
|[Base URL Path Sharing](#base-url-path-sharing)|[974119](https://mseng.visualstudio.com/DefaultCollection/CSI/_workitems?id=974119&_a=edit)|Brady Gaster, Zhiliang Xu|Onboarders, PowerShell docs|
|[Setup official MicrosoftDocs REST repo](#setup-official-microsoftdocs-rest-repo)|[1002795](https://mseng.visualstudio.com/CSI/_workitems?id=1002795&_a=edit)|Brady Gaster, Ying Hua, Jessie Huang|REST Customers and partners outside of Azure|
|[PowerShell Return Types Link to .NET Type](#powershell-return-types-link-to-.net-type)|[983804](https://mseng.visualstudio.com/CSI/_workitems?id=983804&_a=edit)|Brady Gaster, Alice Wang, Sanketh Arvapaly|PowerShell customers and partners|
|[REST API JSON schema display and model navigation](#rest-api-json-schema-display-and-model-navigation)|[949859](https://mseng.visualstudio.com/CSI/_workitems?id=949859&_a=edit)|Brady Gaster, Alice Wang, Sanketh Arvapaly|REST customers and partners|
|[Support documentation of REST enum values](#support-documentation-of-rest-enum-values)|[950650](https://mseng.visualstudio.com/CSI/_workitems?id=950650&_a=edit)|Brady Gaster, Ying Hua, Jessie Huang|REST Customers and partners|



![resources](media/resources.png)

- [OPS Yammer Group](https://www.yammer.com/microsoft.com/#/threads/inGroup?type=in_group&feedId=7133984)
- [OPS docs](https://opsdocs.azurewebsites.net/en-us/opsdocs/index?branch=master)
- [DRAFT Onboarding guides](https://review.docs.microsoft.com/en-us/help/contribute/)
- DL: Join [this group](http://idwebelements/GroupManagement.aspx?Group=ceapexsprint&Operation=join) to subscribe to this sprint summary!
 
![feature-details](media/feature-details.png)

## Enable bilingual publishing for CEO

Enables bilingual (formerly known as SxS) for localized content in the integrated OpenLoc-iCMS pipe (codename: CEO).

***

## Aggregate AirLoc HB messages in OpenLoc to avoid HB problems

This fix is specific to APEX International's AirLoc implementation; AirLoc's frequent api calls to OpenLoc caused handback failures. This issue should not occur in CEO (different workflow/architecture).

***

## Create Loc HO xliff from ecmaxml

This is completes support for intellisense/mref localization. In a nutshell, the workflow is as follows:
- dlls are dropped to a location, and reflection is run to generate ecmaxml files in the en-US repo
- OpenLoc monitors the en-US repo, and generates xliff files for localization
- after files are localized, OpenLoc converts them back to ecmaxml in the loc repos
- both loc and en-us build from the ecmaxml files (they are converted to yaml during the build process, but the yaml files are discarded)
Following this model will allow end user community contributions for localized mref (on the ecmaxml files) in the future.

***

## Automatically update zip file 

The en-US repos contain links to topics outside their own repo, and place a mapping with these xref links into zip files. Since loc often localizes a subset of en-US content, we may not have the same amount of loc topics, and our zip files need to contain more mapped links than the en-US zip files. This feature automates the creation/updating of the zip packages with the correct number of links for loc.

***

## MREF Intellisense in CEO pipe

MREF/Intellisense is currently not enabled in the new iCMS pipe; this feature will enable it.

*** 

## Do not delete referenced arts in CEO pipe

When loc files reference localized art pieces, and the writer deletes the en-US art, OpenLoc also deletes the loc art. The localized file can then no longer pull in the loc art, since it was deleted. The result is broken art in published content. This is fixed in the standalone OL pipe, but needs to be handled for the new iCMS pipe.

***

## Validate YML header before handoff

YML header validation before transforming the file to xliff for localization. Currently, YML header is not validated, file is localized, and then the transform back to markdown breaks after handback. 

***


## Offline Book: Support "view online" page for not-downloaded (OPS) topic

Today there's a broken experience in offline book for OPS content.

When a downloaded topic link to a not-downloaded topic, HelpViewer will show up a "Cannot find requested topic on your computer" page, which prompt user either to "view the topic online" or to "download content".
This prompt experience is as expected. But if the not-downloaded topic is a OPS topic, "view the topic online" is in fact a broken link, which means that user will see 404 after click that link.

This kind of broken experience appear frequently for VS2017 HelpViewer users.

This feature is to update the interface between offline book new tooling and HelpViewer, to let HelpViewer know the correct link of "view the topic online".

The offline book tooling part work is finished with S118 deliverables.
Now it's waiting for HelpViewer's deployment to have this feature functional End-to-End.


***

## Moniker Management in the OPS portal

With the introduction of the API Browser and a number of other versioned content pieces to docs.microsoft.com, we want to make sure that we can easily associate them with individual products with the help of monikers. Previously, to create new monikers, you would have to ping engineers that would provision the data store with the right information. The OPS team since implemented a portal extension that allows moniker management directly without middle-man involvement.

You can take a peek at the feature [on the staging OP portal site](https://opportal-internal.azurewebsites.net/#/monikers):

![Moniker Manager](media/s118/monikermanager.PNG)

***

## Support CNTK Python API reference documentation

No Python API documentation is currently hosted on docs.microsoft.com. DocFX reference materials so far doesn’t support generating Python API documentation. CNTK python API reference docs is currently on https://cntk.ai/pythondocs/apireference.html built with Sphinx using a theme provided by Read the Docs.       
To support CNTK Python API reference documentation to docs.microsoft.com, 
* Eric Holscher from Read the Docs builds a Sphinx-DocFX-YAML converter which can convert python API to DocFX readable YML files. DocFX will consume these YML files to generate yml files for OPS.    
* We built a new DocFX processor for python. Actually this processor can support Python, JavaScript, C# and so on. It can save us a lot of effort on creating new processors and template for new ref languages. 
* We built a new template for python. 
We are building a new documentation experience for Python API customers.

***

## Conceptual Versioning

We first started rolling out versioning of reference content during a previous sprint, as part of the .NET API Browser and PowerShell reference work. We're now working towards enabling broad support for versioning of conceptual content. We're building this on top of the work done for reference and extending it to handle the unique challenges around conceptual. This work will take multiple sprints to roll out in full. Currently, our implementation plan is ready and work is now starting towards the first parts of the Separated Versioning strategy.

**More info**<br>
[The Conceptual Versioning Spec is Available Here](https://review.docs.microsoft.com/en-us/new-hope/specs/ops/conceptual-versioning)

***

## Markdown: Content Switcher

We're working on a new feature that would enable writers to created "tabbed" content, enabling customers to read different "flavors" of the same topic. Imagine that you want to teach someone how to create a virtual machine. Your readers may want to do that with PowerShell, the Azure CLI or the Azure Portal. Today this content has to be split across multiple articles and there is no way to share content between them. The Content Switch feature will address these issues.

**More info**<br>
[The Content Switcher Spec is Available Here](https://review.docs.microsoft.com/en-us/new-hope/specs/conceptual/tabbed-conceptual)

***

## Interactive Tutorials

Interactive Tutorials are a new form of conceptual content that build on our existing foundation. A Tutorial takes a customer through an interactive, step-by-step experience. It features a custom landing page, rich with contextual information related to the tutorial, an in-page step-by-step process, persistent progress tracking, interactive CLIs/REPLs, and more.

**More Info:**<br>
[The Interactive Tutorial Spec is Available Here](https://review.docs.microsoft.com/en-us/new-hope/specs/conceptual/interactive-guides)

***

## Interactive C# REPL

Similar to the work done for the Azure Cloud Shell, we're now working with the .NET team to implement a browser-based C# REPL experience directly into our documentation. This would allow writer-selected code snippets to feature a "Try It" button that would enable running the C# code and seeing the output directly within the browser.

***

## 404 Page

We're working on a new 404 page for docs that provides a modern, fun experience for our customers. We'll be meeting with leadership soon to approve the final approach, polish it and make a plan to ship it. Stay tuned for more information and get your gamepads ready...

***

## Enable SideXSide mouse hover-over experience

SideXSide mouse hover-over feature is ready and tested, it ia a way for our customers to hover-over any localized segment and see the equivalent text in English. We are now covering 100% of all segments.

## Enable-right-to-left-support-for-content
RTL support as enabled only to hub pages. it is now enabled for content. The first team to use it is Dynamics, the feature is tested and works great on all content sections.

## PRMerger Gauntlet Integration

The current PRMerger tool, which provides automated pull request review and merging if certain criteria are met, has been integrated into Gauntlet and enters UAT in the sql-docs-pr repo the first week of Sprint 119. Also onboarding to this repo is the PR review team and Acrolinx. Once UAT has been passed, the new PR Merger will be rolled out to azure-docs-pr, then other content sets.

**More info:**<br>
http://aka.ms/prmergeroverview

***

## Gauntlet Release to Production

The Gauntlet authoring services and VS Code extension is now released to production and available to any Mocrosoft employee working in Markdown and publishing to docs.microsoft.com. Gauntlet provides Markdown authoring assistance to writers working in OPS and publishing to docs.microsoft.com. It includes several functions, such as applying templates to new Markdown files, applying common formatting to strings, and inserting links, images, tokens, snippets, tables, and lists, as well as previewing content for docs.

![](media/S116/gauntlet-toolbar.png) 

**More info**<br>
[Gauntlet Home](http://aka.ms/Gauntlet)<br>
[http://aka.ms/GauntletDocs](http://aka.ms/GauntletDocs)<br>
Questions? Want to be a dogfooder for new features? Email gauntletPM@microsoft.com.

## Gauntlet Metadata Validation

Gauntlet metadata validation, including BI metadata and SEO metadata, is now in UAT with a limited set of dogfooders. It is expected to release to production In June. This feature allows content team admins to configure validation rules in the Gauntlet web UI, and writers and other contributors to validate their files via the Gauntlet VS Code extension.

Additional validations, including Markdown and HTML content validation, are in expected to release over the next few sprints.

**More info:**<br>
http://aka.ms/gauntletdfdocs

***

## Gauntlet Telemetry

We are implementing basic telemetry for the Gauntlet VS Code extension to track usage and better inform feature prioritization in the future.

**More Info:**<br>
[spec](https://review.docs.microsoft.com/en-us/new-hope/specs/gauntlet/gauntlet-telemetry-v1)

***

## Script to build master redirect file

The number of blank Markdowns with just metadata tag `redirect_url` is increasing and these files are unnecessarily being published and stored in repos. For example azure-docs-pr has approximately 1400+ such files that are being redirected. The repo size is already increasing with large number of articles and blank files are just adding to that size. To address this we are creating a Gauntlet VS Code command to file all files with the `redirect_url` tag, build a master redirect file, and then remove the individual files. 

**More Info:**<br>
[spec](https://review.docs.microsoft.com/en-us/new-hope/specs/gauntlet/gauntlet-master-redirect)

## Improve REST API Parameter Layout

We have had a lot of partner and customer asks to improve the overall REST API layout. Things like the nested parameter structure of deep models have been confusing for customers and frustrating for partners. With design being completed during S118 on a better rendering of the parameter display we'll be able to start UX implementation during S119.  

## Support x-parameterized-host

Azure partners making use of the x-ms-parameterized-host swagger extension are currently having their URLs shown incorrectly in the REST API reference. This is blocking their onboarding. 

## Azure Node.js SDK

We will complete the Node.js SDK reference documentation to support the OpenDev event in June. 

## Base URL Path Sharing

Ability for different docsets/repositories to be able to share the same URL base path (dmc/powershell) so that we can have multiple repositories that comprise one reference docset. 

## Setup official MicrosoftDocs REST repo

The current REST API docset resides in a GitHub repository in the Azure organization. We have new partners like HealthVault and Bot Framework who want to bring their APIs to the docs REST API reference site so we are moving the repository to the MicrosoftDocs organization so APEX staff can more easily maintain the repository and unblock partners who would prefer not to be in the Azure organization. 

## PowerShell Return Types Link to .NET Type

For the PowerShell reference topics, there are a few methods such as Get-AzureRmStorageAccount that return simple .NET types. In this case, the method returns a System.String instance. However, our UX doesn't render the return type. 

We will change the UX so that it displays the return type when the type is a simple .NET type identified in the .NET reference. When there is a type (like string, integer, or stream, for example) that have legitimate direct URLs to their corresponding .NET reference pages, we will show the return types as links to their .NET pages. 

## REST API JSON schema display and model navigation

We implemented the x-ms-example support to enable JSON representation display of REST APIs. We need to re-label the x-ms-example section so that it more clearly identifies itself as schema as a JSON representation and not "example." 

We'll also make the JSON display an interactive navigation tool. When users move over model structures displayed in the JSON a visual cue will appear. When clicked, users will navigate lower in the page to the section describing each property in the model. This gives users a snapshot display (the JSON schema view) that enables navigation to deeper information (the parameter table below). 

## Support documentation of REST enum values

Partners need a way to document each available value of an enum. The Azure SDK team is extending the x-ms-enum extension so that Swagger owners can describe the purpose or usage of a particular enum value. We will begin showing this description to the user when the Swagger contains a description. 

## LEAVE (Un-subscribe)
http://idwebelements/GroupManagement.aspx?Group=ceapexsprint&Operation=leave 

## JOIN (Subscribe)
http://idwebelements/GroupManagement.aspx?Group=ceapexsprint&Operation=join 
