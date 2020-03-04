#VSC Sprint 110 Deliveries

Implementation time range for Sprint 110: Nov 21 2016 - Dec 9 2016

Deployment Date for Sprint 110: Dec 12 2016

##Summary for S110

|Area                  | S110 Goal |
| :--- | :---|
| OPS Conceptual | Complete self-service onboarding and enable users to update their docset and repo properties. |
| OPS Reference | Delivery Azure Node.js SDK POC site; Support conceptual + refernce into single TOC for Azure CLI|
| LOC |Xamarin MD extension support, bilingual support for xliff 2.0, improve handoff and localizaiton publish experience|
|Business Continuity|Finish POC as input to make plan for MSDN/TN legacy library migration plan; Keep Maintaining MSDN/TN|


##1 Publishing Service

###1.1 Open Publishing Platform

Features delivered by Sprint 110:

| ID                  | Title | SPEC/Demo Link|
| :--- | :---|:---|
|[653972](https://mseng.visualstudio.com/VSChina/_workitems/edit/653972)|[OPS] Preview PR messages should be configurable| |
|[651938](https://mseng.visualstudio.com/VSChina/_workitems/edit/651938)| [OPS] Support branch fallback||
|[754128](https://mseng.visualstudio.com/VSChina/_workitems/edit/754128)|[DOCS][SEO] Add x-default tag into DOCS sitemap| |
|[754136](https://mseng.visualstudio.com/VSChina/_workitems/edit/754136)|[DOCS][SEO] Add validation to make sure all GoneLive docset has sitemap xml file generated|- |
|[631327](https://mseng.visualstudio.com/VSChina/_workitems/edit/631327)|[OPS] Option to suppress author information at the topic level - Metadata Support| |


Features under working but not able to complete in Sprint 110:

| ID                  | Title | SPEC/Demo Link|
| :--- | :---|:---|
|[638829](https://mseng.visualstudio.com/VSChina/_workitems/edit/638829)|[Open Publishing][Build] Expose build/publishing progress| |
|[786039](https://mseng.visualstudio.com/VSChina/_workitems/edit/786039)|Provide OPS publishing "event log" (for Sitemap & SkyEye)| |
|[484126](https://mseng.visualstudio.com/VSChina/_workitems/edit/484126)|[OPS][Build] I can have incremental build and publishing (functionality for pre-Connect + bugfixing & re-design for post-Connect)| |
|[664331](https://mseng.visualstudio.com/VSChina/_workitems/edit/664331)|[OPS][Build] FY17Q2 Performance Tuning| |

###1.2 Reference Content Publishing

Features delivered by Sprint 110:

| ID                  | Title |SPEC/Demo Link|
| :--- | :---|:---|
|[597223](https://mseng.visualstudio.com/VSChina/_workitems/edit/597223)|List of derived classes has disappeared from the documentation|[Demo](https://microsoft.sharepoint.com/teams/Visual_Studio_China/Shared%20Documents/Forms/AllItems.aspx?id=%2Fteams%2FVisual%5FStudio%5FChina%2FShared%20Documents%2FSprint%20Reviews%2FFeature%5FVideos%2FReference%5FContent%5FPublishing%2FRef%20Sync%20%2D%20Technical%20%2D%20Monday%2C%20December%2012%2C%202016%204%2E32%2E37%20PM%2Emp4&parent=%2Fteams%2FVisual%5FStudio%5FChina%2FShared%20Documents%2FSprint%20Reviews%2FFeature%5FVideos%2FReference%5FContent%5FPublishing) |
|[712096](https://mseng.visualstudio.com/VSChina/_workitems/edit/712096)|For better BI reporting ms.Service BI tag should be configured at module level so that we can tag appropriate service|[Demo](https://microsoft.sharepoint.com/teams/Visual_Studio_China/Shared%20Documents/Forms/AllItems.aspx?id=%2Fteams%2FVisual%5FStudio%5FChina%2FShared%20Documents%2FSprint%20Reviews%2FFeature%5FVideos%2FReference%5FContent%5FPublishing%2FRef%20Sync%20%2D%20Technical%20%2D%20Monday%2C%20December%2012%2C%202016%204%2E32%2E37%20PM%2Emp4&parent=%2Fteams%2FVisual%5FStudio%5FChina%2FShared%20Documents%2FSprint%20Reviews%2FFeature%5FVideos%2FReference%5FContent%5FPublishing) |
|[711827](https://mseng.visualstudio.com/VSChina/_workitems/edit/711827)|[REST] Support “externalDocs" in Swagger| |
|[711844](https://mseng.visualstudio.com/VSChina/_workitems/edit/711844)|[REST] Support “example" in Swagger| |
|[711842](https://mseng.visualstudio.com/VSChina/_workitems/edit/711842)|[REST] Add “remarks" in Overwrites| |
|[696832](https://mseng.visualstudio.com/VSChina/_workitems/edit/696832)|[Azure CLI] Enable index.md-style, conceptual home page markdown capabilities|[Demo](https://microsoft.sharepoint.com/teams/Visual_Studio_China/Shared%20Documents/Forms/AllItems.aspx?id=%2Fteams%2FVisual%5FStudio%5FChina%2FShared%20Documents%2FSprint%20Reviews%2FFeature%5FVideos%2FReference%5FContent%5FPublishing%2FAzureCli%2DConceputal%2DSupport%2Ewebm&parent=%2Fteams%2FVisual%5FStudio%5FChina%2FShared%20Documents%2FSprint%20Reviews%2FFeature%5FVideos%2FReference%5FContent%5FPublishing) |
|[711861](https://mseng.visualstudio.com/VSChina/_workitems/edit/711861)|[REST] Test and Transform GFM Syntax in Swagger Descriptions| |
|[711884](https://mseng.visualstudio.com/VSChina/_workitems/edit/711884)|Categories for SDK Docsets|[Demo](https://microsoft.sharepoint.com/teams/Visual_Studio_China/Shared%20Documents/Forms/AllItems.aspx?id=%2Fteams%2FVisual%5FStudio%5FChina%2FShared%20Documents%2FSprint%20Reviews%2FFeature%5FVideos%2FReference%5FContent%5FPublishing%2FRef%20Sync%20%2D%20Technical%20%2D%20Monday%2C%20December%2012%2C%202016%204%2E32%2E37%20PM%2Emp4&parent=%2Fteams%2FVisual%5FStudio%5FChina%2FShared%20Documents%2FSprint%20Reviews%2FFeature%5FVideos%2FReference%5FContent%5FPublishing) |

Features under working but not able to complete in Sprint 110:

| ID                  | Title |SPEC/Demo Link|
| :--- | :---|:---|
|[653877](https://mseng.visualstudio.com/VSChina/_workitems/edit/653877)|[OPS][Reference] use inline code for language keywords and parameter references from triple slash comments instead of \<strong> and \<em>| |
|[712193](https://mseng.visualstudio.com/VSChina/_workitems/edit/712193)|[PowerShell] Enable configuration for enabling/disabling external contribution by repo in powershell on Docs| |
|[711914](https://mseng.visualstudio.com/VSChina/_workitems/edit/711914)|[DocFX] [Reference] Azure Node.js SDK| |


###1.3 Open Publishing Portal


Features under working but not able to complete in Sprint 110:

| ID                  | Title |SPEC/Demo Link|
| :--- | :---|:---|
|[655649](https://mseng.visualstudio.com/VSChina/_workitems/edit/655649)|[OPS] [Provisioning] [New Portal] UX updates based on customer feedback| [Request a new locale](../partnerdocs/localization/loc_request-new-locale.md), [search by repo and have a repo view](../opsportal.md), and view [pull requests](../partnerdocs/publish.md#PullRquest) |
|[656288](https://mseng.visualstudio.com/VSChina/_workitems/edit/656288)|[OPS] [Provisioning] [New Portal] [New functionality] I can edit docset or repo properties for a single or multiple locales at once| [Disconnect a repo from OPS](../partnerdocs/edit-repo-properties.md), [disconnect a docset from OPS](../partnerdocs/edit-docset-properties.md), [edit repo properties](../partnerdocs/edit-repo-properties.md), [edit docset properties](../partnerdocs/edit-docset-properties.md) |


###1.4 Offline Book

Features delivered by Sprint 110:

| ID                  | Title |SPEC/Demo Link|
| :--- | :---|:---|
|[754157](https://mseng.visualstudio.com/VSChina/_workitems/edit/754157)|[Offline Book] Integrate with OPS content pattern| |



##2 Standalone Service
###2.1 Open Localization Service

Features delivered by Sprint 110:

| ID                  | Title |SPEC/Demo Link|
| :--- | :---|:---|
|[655210](https://mseng.visualstudio.com/VSChina/_workitems/edit/655210)|[OPS][OL] BLMT to support xliff 2.0| |
|[704182](https://mseng.visualstudio.com/VSChina/_workitems/edit/704182)|[LOC] [OL] [VSC] Update HO repo when loc config is updated| |
|[704719](https://mseng.visualstudio.com/VSChina/_workitems/edit/704719)|[LOC] [OL] [VSC]  Xamarin MD extension support| |
|[711973](https://mseng.visualstudio.com/VSChina/_workitems/edit/711973)|[OPS][Validation] [DCR] Hub and Landing pages need less restrictive validation+ adddress false positives in build validation | |



Features under working but not able to complete in Sprint 110:

| ID                  | Title |SPEC/Demo Link|
| :--- | :---|:---|
|[655185](https://mseng.visualstudio.com/VSChina/_workitems/edit/655185)|[OPS][OL] OL-iCMS phase 2| |



###2.2 DocFX (Open Source)
No new feature in this sprint.

###2.3 Rating & Commenting & SideNotes
No new feature in this sprint.

##3 Tooling

###3.1 CAPS->OPS Migration Tool

Features delivered by Sprint 110:

| ID                  | Title |SPEC/Demo Link|
| :--- | :---|:---|
|[711824](https://mseng.visualstudio.com/VSChina/_workitems/edit/711824)|CAPS Markdown Exporter: integrate non-migrating topic link fix solution into Exporter|N/A|

###3.2 DPS->OPS Migration Tool
No new feature in this sprint.

###3.3 CAPS

No investment in FY17Q2.

##4 Data Insights

Features under working but not able to complete in Sprint 110:

| ID                  | Title |SPEC/Demo Link|
| :--- | :---|:---|
|[513197](https://mseng.visualstudio.com/VSChina/_workitems/edit/513197)|[BI]MSDN/Docs Engineer BI support| |
|[629953](https://mseng.visualstudio.com/VSChina/_workitems/edit/629953)|[Instrumentation] Site instrumentation updates [CSI-Share]| |
|[658278](https://mseng.visualstudio.com/VSChina/_workitems/edit/658278)|[BI][Q2] Updates to user inventory service [CSI-Share]| |


##5 Business Continuity

Features to be delivered by Sprint 110:

| ID                  | Title |SPEC/Demo Link|
| :--- | :---|:---|
|[711895](https://mseng.visualstudio.com/VSChina/_workitems/edit/711895)|Docs Vanilla - Proof of Concept| |
|[634962](https://mseng.visualstudio.com/VSChina/_workitems/edit/634962)|[Site Search] Update to modern Bing API 5.0|N/A|
|[671762](https://mseng.visualstudio.com/VSChina/_workitems/edit/671762)|[Forums] EE - SDL phase1&2|N/A|
|[671766](https://mseng.visualstudio.com/VSChina/_workitems/edit/671766)|[Recognition] EE - SDL phase1&2|N/A|
|[650416](https://mseng.visualstudio.com/VSChina/_workitems/edit/650416)|[BLOG] EE - SDL phase 1&2|N/A|
