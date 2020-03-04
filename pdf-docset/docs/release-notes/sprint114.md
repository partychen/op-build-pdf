#APEX China Sprint 114 Summary Report

## Time Range

Implementation time range for Sprint 114:  Feb 13 2017 - March 3 2017

Deployment Date for Sprint 114:  March 6 2017


## Deliverables
### User Facing Deliverables
User facing deliverables means the delivery items that having user impact, externally or internally.

- **Xamarin POC site** (Feature [786738](https://mseng.visualstudio.com/VSChina/_workitems/edit/786738), Feature [796693](https://mseng.visualstudio.com/VSChina/_workitems/edit/796693)):

>[!Note]
>This deliverable impacts End User and .NET REF content writer

The new URL of POC site is: https://ppe.docs.microsoft.com/en-us/fulldotnet/system.io.directory?branch=master

Back-end work and migration tool are all ready. 

E2E remaining work is at front-end side and integration work.

For the detailed update please refer to the OneNote [here](https://microsoft.sharepoint.com/teams/Visual_Studio_China/_layouts/15/WopiFrame.aspx?sourcedoc={2438313c-56db-4aa3-be47-eac50e7bba32}&action=edit&wd=target%28Reference%2Eone%7C89ABDA27-A295-452D-8E15-15B44A2FEA8A%2FXamarin%20POC%20site%20update%7C1BB33A75-B69D-4304-B195-6928E850CC6D%2F%29onenote%3Ahttps%3A%2F%2Fmicrosoft%2Esharepoint%2Ecom%2Fteams%2FVisual_Studio_China%2FShared%20Documents%2FDOCS%2EMSFT%2FReference%2Eone#Xamarin%20POC%20site%20update&section-id={89ABDA27-A295-452D-8E15-15B44A2FEA8A}&page-id={1BB33A75-B69D-4304-B195-6928E850CC6D}&end).

- **LOC meta for migration** (Feature [893657](https://mseng.visualstudio.com/VSChina/_workitems/edit/893657))

>[!Note]
>This deliverable impacts IPM  

Please follow below step to generate translation-state file for vsdocs/vsppdocs loc repo. 

  1. Update Mode to “gents” in migration tool info configuration. 

  2. Under this mode, metadata from en-us will be copied to loc content and translation-state file will be generated. No content will be re-exported.

  3. Sync en-us repo & Loc repo (switch to the branch with migrated content)

  4. Run tool. 

  5. Add/Commit the changes and push to loc repo branch.

  6. Send PR to IPM for review


- **Hosting API to unblock front-end versioning implementation** (Feature [924038](https://mseng.visualstudio.com/VSChina/_workitems/edit/924038), Feature [660294](https://mseng.visualstudio.com/VSChina/_workitems/edit/660294))

>[!Note]
>This deliverable impacts Docs front-end (Duncan Mackenzie) dev team  

This Hosting API work is a part of versioning feature that having user impact. Given that versioning feature is not End-to-End ready yet, this delivery don't have impact to end user at this moment, but can help to unblock front-end engineering work (Duncan Mackenzie).

See below document for how to call the moniker-related API's.

[Versioning APIs](onenote:https://microsoft.sharepoint.com/teams/Visual_Studio_China/Shared Documents/DOCS.MSFT/Engineering.one#Versioning%20APIs&section-id={4A1B929F-04DD-4DE1-895C-8B803146724B}&page-id={C35716F7-E706-464D-BD73-D5EBA4453A80}&end)  ([Web view](https://microsoft.sharepoint.com/teams/Visual_Studio_China/_layouts/OneNote.aspx?id=%2Fteams%2FVisual_Studio_China%2FShared%20Documents%2FDOCS.MSFT&wd=target%28Engineering.one%7C4A1B929F-04DD-4DE1-895C-8B803146724B%2FVersioning%20APIs%7CC35716F7-E706-464D-BD73-D5EBA4453A80%2F%29))


- **LOC performance** (Feature [799284](https://mseng.visualstudio.com/VSChina/_workitems/edit/799284), Feature [923225](https://mseng.visualstudio.com/VSChina/_workitems/edit/923225))

>[!Note]
>This deliverable impacts IPM 

During the perf testing, we found “batch stage files” operation cost too much times, about 2+ hours to batch stage 44990 files. We did some optimization for that, using git command instead of libgit2sharp to stage files, reduced to 18 seconds for batch stage 44990 files.

>HO time: 2 hours/locale -> 12 minutes/locale

>HB time: 3 hours/locale -> 15 minutes/locale

Detailed performance test report is available in attachment of [Feature 799284](https://mseng.visualstudio.com/VSChina/_workitems/edit/799284).


- **LOC meta for BI** (Feature [893658](https://mseng.visualstudio.com/VSChina/_workitems/edit/893658))

>[!Note]
>This deliverable impacts BI team and IPM 

From the image below, we can see that the *ms.handoffdate* metadata is included in the localized markdown file. For more details, please refer to the attachment in [893658](https://mseng.visualstudio.com/VSChina/_workitems/edit/893658).

![ms.handoffdate metadata](../images/ms_handoffdate.jpg)

- **Build performance** (Feature [798136](https://mseng.visualstudio.com/VSChina/_workitems/edit/798136))

>[!Note]
>This deliverable impacts all content writers

Several improvements has been done in last sprint:

  1. An improvement that speed up git clone time.
  2. Parallel the some I/O tasks like publish and package upload to reduce overall build time.

The publish and PR time on azure-docs-pr after S114 deployment is about **8** minutes.

- **MTPS redirection** (Feature [798263](https://mseng.visualstudio.com/VSChina/_workitems/edit/798263))

>[!Note]
>This deliverable impacts users who want to redirect MTPS page out. The process to request a MTPS redirection is changed a little.

User manual has been updated to include new features:
[Content Lifecycle Management Portal](onenote:https://microsoft.sharepoint.com/teams/Visual_Studio_China/ALPS/Shared Documents/MSDN/MSDN_Transition/MTPS/Feature Spec.one#Content%20Lifecycle%20Management%20Portal&section-id={BB9E7D9E-D5E7-42C2-81CA-A6C835912E03}&page-id={C0653295-9ED7-4DBA-8EB5-94190D97E7DE}&end)  ([Web view](https://microsoft.sharepoint.com/teams/Visual_Studio_China/ALPS/_layouts/OneNote.aspx?id=%2Fteams%2FVisual_Studio_China%2FALPS%2FShared%20Documents%2FMSDN%2FMSDN_Transition&wd=target%28MTPS%2FFeature%20Spec.one%7CBB9E7D9E-D5E7-42C2-81CA-A6C835912E03%2FContent%20Lifecycle%20Management%20Portal%7CC0653295-9ED7-4DBA-8EB5-94190D97E7DE%2F%29))

- **OPS Publishing Journal data** (Feature [786039](https://mseng.visualstudio.com/VSChina/_workitems?id=786039))

>[!NOTE]
>This deliverable impacts BI team as well as Docs Site-Search dev team

This feature enables BI and Site-Search teams to consume the live content updates in a more efficient incremental way. This feature was also known as OPS publishing "event log".

>How to Consume?

>It’s easy to consume the publishing journals - use [Microsoft Azure Storage Explorer](http://storageexplorer.com/) or write your own tool. All journal data for production is in the live Table. You can use the [SAS token](https://docs.microsoft.com/en-us/azure/storage/storage-dotnet-shared-access-signature-part-1) for access.

>SAS token

>`?sv=2015-12-11&ss=bfqt&srt=sco&sp=rl&se=2117-03-01T00:00:00Z&st=2017-03-01T00:00:00Z&spr=https&sig=wvv1Hu66W86OD%2FpmgYQ6hLbjgAqcoEBkEuWNpZi6d%2Bg%3D`
 
>Table service SAS [URL](https://opspublishjournalprod.table.core.windows.net/?sv=2015-12-11&ss=bfqt&srt=sco&sp=rl&se=2117-03-01T00:00:00Z&st=2017-03-01T00:00:00Z&spr=https&sig=wvv1Hu66W86OD%2FpmgYQ6hLbjgAqcoEBkEuWNpZi6d%2Bg%3D)

>`https://opspublishjournalprod.table.core.windows.net/?sv=2015-12-11&ss=bfqt&srt=sco&sp=rl&se=2117-03-01T00:00:00Z&st=2017-03-01T00:00:00Z&spr=https&sig=wvv1Hu66W86OD%2FpmgYQ6hLbjgAqcoEBkEuWNpZi6d%2Bg%3D`

- **PR Validation Improvement** (Bug [939575](https://mseng.visualstudio.com/dfe297d9-5f61-4d42-b4bb-03f8b8646944/_workitems?id=939575))

>[!NOTE]
>This deliverable impacts all content writers

There're a few feedback from partners about PR validation comments, the main issues are:

  1. Some files like include files are not shown in PR comment, thus there is no way to see the warnings in those files.

  2. Some type of files like TOC and images does not a good preview link.

To improve PR validation usability, the following information are added to the PR validation comment to address the above issues:

  1. Articles, no change.

  2. TOCs, preview of TOC of will an article that contains the TOC, preferably within changed files.

  3. Resources (images), preview of resource of will an article that uses this resource, preferably within changed files.

  4. Tokens/code snippets, will be seprate entries in PR comment, preview of token/code snippet will be an article that include this token/code snippet, preferably within changed files. If there is any warning within the token, it will shown under the token in PR comment.

  5. Other files (like config), show in PR comment but without any preview url.

Here is a sample [PR](https://github.com/Microsoft/openpublishing-docs/pull/181) that include the changes above.

### EE Deliverables

- **Dynamic Rendering** (Feature [639814](https://mseng.visualstudio.com/VSChina/_workitems/edit/639814)) 

Code ready. 

Plan to roll out since S115 partner by parnter. 
The rolling out has no impact to partner teams or users. But has impact to Docs Front-end Dev Team, i.e. each time when templating is changed, front-end dev team don't need to apply the new template to repos swiched to dynamic rendering anymore.

Hosting team (Zhiliang XU) will keep Docs front-end (Duncan Mackenzie) dev team synced.

## In-Progress

Below features are under working as planned.

| Title                  | ID |
| :--- | :---|
|Powershell March release |[924038](https://mseng.visualstudio.com/VSChina/_workitems/edit/924038)|

## Dependency/Postponed

Below features have external dependency or specific postpone reasons.

| Title| ID | Status|
| :--- | :---| :---|
|[Docs] API Browser|[924060](https://mseng.visualstudio.com/VSChina/_workitems/edit/924060)|Code ready, but wait for integration with front-end.|  
|Namespace in API Browser|[926223](https://mseng.visualstudio.com/VSChina/_workitems/edit/926223)|Code ready, but wait for integration with front-end.|
|[Offline Book] Run pilot project with CSI (as partner validation)|[785016](https://mseng.visualstudio.com/VSChina/_workitems/edit/785016)|More scenarios are identified during pilot project, so need more time to deliver tooling fixes. In addtion, **per version book** is identified as a missing feature ([938097](https://mseng.visualstudio.com/VSChina/_workitems/edit/938097)) and is put as S115 potential request.|
|Windows iroot on MSDN and TechNet requires UHF end point update|[655706](https://mseng.visualstudio.com/VSOnline/_workitems?id=655706)|Code ready. Dependent on UHF bug fixing to unblock our rolling out.|


