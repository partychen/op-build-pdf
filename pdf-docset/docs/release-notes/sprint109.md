#VSC Sprint 109 Deliveries

Implementation time range for Sprint 109: Oct 31 2016 - Nov 18 2016

Deployment Date for Sprint 109: Nov 21 2016

##Notice
- Deployment cadence is more frequent in Sprint 109 for hotfixes

##Summary for S109
- Smooth the content GoLive for Connect(), including Azure, VS2017RC, ASP.NET, and EF
- 5X OPS build and publish perf improvment is achieved in Sprint 109
- Cont. feature development as per FY17Q2 planning


##1 Publishing Service

###1.1 Open Publishing Platform

| ID                  | Title | SPEC/Demo Link|
| :--- | :---|:---|
|[664331](https://mseng.visualstudio.com/DefaultCollection/VSChina/_workitems/edit/664331)|[OPS][Build] Performance Tuning (Continuous Improvement work)|N/A|
|[651938](https://mseng.visualstudio.com/DefaultCollection/VSChina/_workitems/edit/651938)| [OPS] Support branch fallback (investigation in S109) |N/A|
|[660294](https://mseng.visualstudio.com/DefaultCollection/VSChina/_workitems/edit/660294)|I can have Content Versioning - Multi Version Docset and Topic (infrastructure work in S109)|SPEC link in TFS|
|[519371](https://mseng.visualstudio.com/VSChina/_workitems/edit/519371)|[OPS] [docs]Allow GitHub contributor info to be suppressed in OP for pseudo contributors.|SPEC link in TFS |
|[650338](https://mseng.visualstudio.com/VSChina/_workitems/edit/650338)|[OPS] support F1 query service for DOCS.MSFT|[OPS content meta for F1 Query Service](https://opsdocs.azurewebsites.net/en-us/opsdocs/partnerdocs/f1-query?branch=master) |


###1.2 Reference Content Publishing

| ID                  | Title |SPEC/Demo Link|
| :--- | :---|:---|
|[697100](https://mseng.visualstudio.com/VSChina/_workitems/edit/697100)|[DocFx] Expose UID as metadata 'ms.assetID' field for all ref generated and published thru OPS|[Sample page on "ms.assetid" in OPS Reference document](https://microsoft.sharepoint.com/teams/Visual_Studio_China/_layouts/15/WopiFrame.aspx?sourcedoc={824ce5b2-baea-4bca-a196-de481d3c223b}&action=edit&wd=target%28Features%2Eone%7CA1366F0F%2D4F98%2D40ED%2D98C0%2D4EA3A6176A95%2FMeta%20for%20Reference%20Doc%7CA0DBB5AD%2D06AE%2D4E07%2D8E10%2DB18E73ABFA5D%2F%29) |

###1.3 Open Publishing Portal
| ID                  | Title |SPEC/Demo Link|
| :--- | :---|:---|
|[655649](https://mseng.visualstudio.com/DefaultCollection/VSChina/_workitems/edit/655649)|[OPS][Provisioning][New Portal] UX updates based on customer feedback (cross sprints work) | [OPS portal page](../OPSPortal.md) |
|[656288](https://mseng.visualstudio.com/DefaultCollection/VSChina/_workitems/edit/656288) | [OPS] [Provisioning] [New Portal] [New functionality] I can edit docset or repo properties for a single or multiple locales at once (cross sprints work)| [OPS portal page](../OPSPortal.md), [docset editing spec](../specdocs/OPS_Portal_Docset-Property-Editing.md), [repo editing spec](../specdocs/OPS_Portal_Repo-Property-Editing.md) |
|[661221](https://mseng.visualstudio.com/DefaultCollection/VSChina/_workitems/edit/661221)|[OPS] [Provisioning] Setup and move repos to new Docs GitHub organization (Executing 1 of 3)|N/A|

###1.4 Offline Book
| ID                  | Title |SPEC/Demo Link|
| :--- | :---|:---|
|[641246](https://mseng.visualstudio.com/DefaultCollection/VSChina/_workitems/edit/641246)|[Offline Book] phase3 - system ready | [Demo on Offline Book new tooling](https://microsoft.sharepoint.com/teams/Visual_Studio_China/_layouts/15/guestaccess.aspx?guestaccesstoken=LS5etk09GC5JWQxwc0B8oXKJZD3H7FsiMS%2booTgbDc0%3d&docid=2_092fc74326d3b40a3962c7125baa1095b&rev=1), [Deck used in the Demo](https://microsoft.sharepoint.com/teams/Visual_Studio_China/_layouts/15/guestaccess.aspx?guestaccesstoken=cBbSPcsoTdxx8QlGchNhPXzxdYNggPz2jtfdd0RosoM%3d&docid=2_08cf7655654a94505ba1e99586d935f23&rev=1)|



##2 Standalone Service
###2.1 Open Localization Service

| ID                  | Title |SPEC/Demo Link|
| :--- | :---|:---|
|[693614](https://mseng.visualstudio.com/VSChina/_workitems/edit/693614)|[Loc] VSC: Enable priority filter in Force Handoffs|N/A|
|[688202](https://mseng.visualstudio.com/VSChina/_workitems/edit/688202)|[LOC] VSC: Remove <Target> element content in xliff HO files|[Sample HO Xliff files](https://github.com/Microsoft/azure-docs-pr.handoff/commit/8510fec1b9fe917f085d868ff5187287cce27d28)|

###2.2 DocFX (Open Source)
No new feature in this sprint.

###2.3 Rating & Commenting & SideNotes
No new feature in this sprint.

##3 Tooling

###3.1 CAPS->OPS Migration Tool
| ID                  | Title |SPEC/Demo Link|
| :--- | :---|:---|
|[692819](https://mseng.visualstudio.com/VSChina/_workitems/edit/692819)|CAPS Markdown Exporter: generate TOC.md based on CAPS TOC structure|N/A|
|[695054](https://mseng.visualstudio.com/VSChina/_workitems/edit/695054)|CAPS Markdown Exporter - add language identifier to snippets on export|N/A|
|[695776](https://mseng.visualstudio.com/VSChina/_workitems/edit/695776)|CAPS Markdown Exporter - leverage Preview export file name mapping to fix cross-repo links|N/A|

###3.2 DPS->OPS Migration Tool
No new feature in this sprint.

###3.3 CAPS

No investment in FY17Q2.

##4 Data Insights

| ID                  | Title |SPEC/Demo Link|
| :--- | :---|:---|
|[629950](https://mseng.visualstudio.com/VSChina/_workitems/edit/629950)|[AB] Updates to content experimentation platform [CSI-Share]|N/A |
|[662479](https://mseng.visualstudio.com/VSChina/_workitems/edit/662479)|[AB] Content experimentation - n topics v. n topics [CSI-Share]|[Custom filter spec](https://microsoft.sharepoint.com/teams/Visual_Studio_China/_layouts/OneNote.aspx?id=%2Fteams%2FVisual_Studio_China%2FShared%20Documents%2FData%20Insights&wd=target%28AB%20Testing.one%7C27370428-2925-4287-BC26-5D15993C66D0%2FUse%20custom%20filter%20to%20choose%20target%20topics%20or%20users%7CA4DADBF4-0B26-46D8-A71E-12B21CDDA25E%2F%29) |
|[662485](https://mseng.visualstudio.com/VSChina/_workitems/edit/662485)|[AB] Content experimentation - targeting [CSI-Share]|[Custom filter spec](https://microsoft.sharepoint.com/teams/Visual_Studio_China/_layouts/OneNote.aspx?id=%2Fteams%2FVisual_Studio_China%2FShared%20Documents%2FData%20Insights&wd=target%28AB%20Testing.one%7C27370428-2925-4287-BC26-5D15993C66D0%2FUse%20custom%20filter%20to%20choose%20target%20topics%20or%20users%7CA4DADBF4-0B26-46D8-A71E-12B21CDDA25E%2F%29) |
|[658278](https://mseng.visualstudio.com/VSChina/_workitems/edit/658278)|[BI][Q2] Updates to user inventory service [CSI-Share]|N/A|


##5 Business Continuity
| ID                  | Title |SPEC/Demo Link|
| :--- | :---|:---|
|[690663](https://mseng.visualstudio.com/VSChina/_workitems/edit/690663)| Add docs domain in msdn search|N/A|
|[671762](https://mseng.visualstudio.com/VSChina/_workitems/edit/671762)|[Forums] EE - SDL (cross sprints work)|N/A|
|[671766](https://mseng.visualstudio.com/VSChina/_workitems/edit/671766)|[Recognition] EE - SDL (cross sprints work)|N/A|
|[655706](https://mseng.visualstudio.com/VSChina/_workitems/edit/655706)|Windows iroot on MSDN and TechNet requires UHF end point update|N/A|
