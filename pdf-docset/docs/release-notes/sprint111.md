#VSC Sprint 111 Deliveries

Implementation time range for Sprint 111: Dec 12 2016 - Dec 30 2016

Deployment Date for Sprint 111: Jan 3 2017

##Summary for Sprint 111

|Area                  | S111 Goal |
| :--- | :---|
| OPS Conceptual | Usability Improvements. Finish docset and repo property editing |
| OPS Reference | Provide Node.js SDK staging site; Provide Node.js CLI POC site; Re-structure Reference Pages|
| LOC | New OL/iCMS pipe: improve publish status,  repo creation and provision for MicrosoftDocs, lockdown scope and user scenarios for Q3 with office team|
| BI | Build time projection for OPS; Data sync enhancement for livefyre|
|Business Continuity| Finish MSDN/TN accessibility bug fixing, and identify gaps for MTPS redirection workflow|


##1 Publishing Service

###1.1 Open Publishing Platform

Features to be delivered by Sprint 111:

| ID                  | Title | SPEC/Demo Link|
| :--- | :---|:---|
|[664331](https://mseng.visualstudio.com/VSChina/_workitems/edit/664331)|[OPS][Build] FY17Q2 Performance Tuning| |
|[584293](https://mseng.visualstudio.com/VSChina/_workitems/edit/584293)|[OPS] Master Redirect File per Docset| |
|[769929](https://mseng.visualstudio.com/VSChina/_workitems/edit/769929)|[OPS][EE] Setup the E2E test process and improve test coverage of OPS |  |
|[790351](https://mseng.visualstudio.com/VSChina/_workitems/edit/790351)|[OPS][Meta]Remove metadata from blacklist: open_to_public_contributors, content_git_url|  |
|[833467](https://mseng.visualstudio.com/VSChina/_workitems/edit/833467)|[OPS][Meta] degrate "author" meta to optional meta|  |


Features under working but not able to complete in Sprint 111:

| ID                  | Title | SPEC/Demo Link|
| :--- | :---|:---|
|[638829](https://mseng.visualstudio.com/VSChina/_workitems/edit/638829)|[Open Publishing][Build] Expose build/publishing progress| |
|[786039](https://mseng.visualstudio.com/VSChina/_workitems/edit/786039)|Provide OPS publishing "event log" (for Sitemap & SkyEye)  |  |
|[639814](https://mseng.visualstudio.com/VSChina/_workitems/edit/639814)|[OPS] Dynamic Rendering for OP.Static and docs.msft.com |[Spec](https://microsoft.sharepoint.com/teams/Visual_Studio_China/_layouts/15/WopiFrame.aspx?sourcedoc={2438313c-56db-4aa3-be47-eac50e7bba32}&action=edit&wd=target%28Engineering%2Eone%7C4A1B929F%2D04DD%2D4DE1%2D895C%2D8B803146724B%2FDynamic%20Rendering%20for%20docs%2Emsft%2Ecom%7CF757CFB1%2D4272%2D418D%2DBAC8%2DBE11C0D622DE%2F%29)|

###1.2 Reference Content Publishing

Features to be delivered by Sprint 111:

| ID                  | Title |SPEC/Demo Link|
| :--- | :---|:---|
|[712193](https://mseng.visualstudio.com/VSChina/_workitems/edit/712193)|[PowerShell] Enable configuration for enabling/disabling external contribution by repo in powershell on Docs  |  |
|[653877](https://mseng.visualstudio.com/VSChina/_workitems/edit/653877)|[OPS][Reference] use inline code for language keywords and parameter references from triple slash comments instead of <strong> and <em> |  |

Features under working but not able to complete in Sprint 111:

| ID                  | Title |SPEC/Demo Link|
| :--- | :---|:---|
|[711914](https://mseng.visualstudio.com/VSChina/_workitems/edit/711914)|[DocFX] [Reference] Azure Node.js SDK | [POC Site](https://ppe.docs.microsoft.com/en-us/azure-sdk-for-node-doc/) |
|[796342](https://mseng.visualstudio.com/VSChina/_workitems/edit/796342)|[DocFX] Re-structure Reference Pages  |  |
|[703588](https://mseng.visualstudio.com/VSChina/_workitems/edit/703588)|[DocFX] Azure XPlat CLI Documentation  | [POC Site](https://ppe.docs.microsoft.com/en-us/azure-xplat-cli-poc/) |
|[861944](https://mseng.visualstudio.com/VSChina/_workitems/edit/861944)|[OPS] [REF] Generate F1 keyword for reference document|  |


###1.3 Repo Management & OPS Portal

Features to be delivered by Sprint 111:

| ID                  | Title |SPEC/Demo Link|
| :--- | :---|:---|
|[655649](https://mseng.visualstudio.com/VSChina/_workitems/edit/655649)|[OPS] [Provisioning] [New Portal] UX updates based on customer feedback| [New publishing history](../partnerdocs/publish.md#PubHistory) |
|[656288](https://mseng.visualstudio.com/VSChina/_workitems/edit/)|[OPS] [Provisioning] [New Portal] [New functionality] I can edit docset or repo properties for a single or multiple locales at once| [edit docset properties](../partnerdocs/edit-docset-properties.md) |

###1.4 Offline Book

Features to be delivered by Sprint 111:

| ID                  | Title |SPEC/Demo Link|
| :--- | :---|:---|
|[800356](https://mseng.visualstudio.com/VSChina/_workitems/edit/800356)|[Offline Help] ToC Nodes without content should list links to child nodes| |

Features under working but not able to complete in Sprint 111:

| ID                  | Title | SPEC/Demo Link|
| :--- | :---|:---|
|[670204](https://mseng.visualstudio.com/VSChina/_workitems/edit/670204)|[Offline Book] Security review for offline book service on Azure |  |
|[861998](https://mseng.visualstudio.com/VSChina/_workitems/edit/861998)|[Offline Books] Investigate the ability to extract first H1 from content as the title for the article.|  |


##2 Standalone Service
###2.1 Open Localization Service

Features to be delivered by Sprint 111:

| ID                  | Title |SPEC/Demo Link|
| :--- | :---|:---|
|[655185](https://mseng.visualstudio.com/VSChina/_workitems/edit/655185)| [OPS][OL] OL-iCMS phase 2 |  |

###2.2 DocFX (Open Source)
No new feature in this sprint.

###2.3 Rating & Commenting & SideNotes
No new feature in this sprint.

##3 Tooling

###3.1 CAPS->OPS Migration Tool

Features to be delivered by Sprint 111:

| ID                  | Title |SPEC/Demo Link|
| :--- | :---|:---|
|[706246](https://mseng.visualstudio.com/VSChina/_workitems/edit/706246)|[CAPS Export] enable incremental migrations for loc | |
|[796560](https://mseng.visualstudio.com/VSChina/_workitems/edit/796560)|[CAPS Export] Export full projects, when available, instead of separate code files| |
|[796561](https://mseng.visualstudio.com/VSChina/_workitems/edit/796561)|[CAPS Export] Ensure that snippet disambiguation is resolved for snippets with the same name| |

###3.2 DPS->OPS Migration Tool
No new feature in this sprint.

###3.3 CAPS

No investment in FY17Q2.

##4 Data Insights

Features under working but not able to complete in Sprint 111:

| ID                  | Title |SPEC/Demo Link|
| :--- | :---|:---|
|[629950](https://mseng.visualstudio.com/VSChina/_workitems/edit/629950)|[AB] Updates to content experimentation platform [CSI-Share]| |
|[658278](https://mseng.visualstudio.com/VSChina/_workitems/edit/658278)|[BI][Q2] Updates to user inventory service [CSI-Share]| |
|[629953](https://mseng.visualstudio.com/VSChina/_workitems/edit/629953)|[Instrumentation] Site instrumentation updates [CSI-Share]| |


##5 Business Continuity

Features to be delivered by Sprint 111:

| ID                  | Title |SPEC/Demo Link|
| :--- | :---|:---|
|[639496](https://mseng.visualstudio.com/VSChina/_workitems/edit/639496)|[MSDN/TN][Web Platform] Accessibility - Align with Microsoft Accessibility Standard|N/A|
|[653167](https://mseng.visualstudio.com/VSChina/_workitems/edit/653167)|Social apps accessibility fix|N/A|

Features under working but not able to complete in Sprint 111:


| ID                  | Title |SPEC/Demo Link|
| :--- | :---|:---|
|[468068](https://mseng.visualstudio.com/VSChina/_workitems/edit/468068)|[Archive]Provide UI tool for customer self-service on redirection/archive/retired| |
|[708457](https://mseng.visualstudio.com/VSChina/_workitems/edit/708457)|Migrate from MSCOM Geo Service to RevIP Service for IP reverse lookup|N/A|
