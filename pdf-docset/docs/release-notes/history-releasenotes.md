# History Release Notes
This page contains information on the functionality released during ***Sprint 91 - Sprint 101*** that affects partners. There are many infrastructure and performance improvements that we deliver that are not necessarily in this list.

## Sprint 101
Open Localization
* Force handoff 
* Update localization hand back report, including adding publish end point 

## Sprint 100
DocFx
* [Template supporting static TOC](https://github.com/dotnet/docfx/issues/245) 
* [Refine template engine](https://github.com/dotnet/docfx/issues/244) 
 
## Sprint 99
* Customizable branch name for contribution button]

DoxFx
* Support generate IntelliSense files
* Support Cross reference for external content
* Enable PowerShell reference documentation rendering
* Support CLI for .net core
* Add code snippet features to match features from sphinx literalinclude directive

## Sprint 98
SEO
* Auto-generate title metadata for MSDN
.* Separate OP sitemap per locale
* Support meta <hreflang>

Open Localization
* To list dependency between ARTICLE and INCLUDES in HB and Loc status report
* Retain HT/MT metadata inside of files, and for first post-migration HO

DocFx
* Support Filter API
* Combine TOC files to output a single TOC

## Sprint 97
* [Feedback and rating for OP pages](../partnerdocs/publishedpages.md)
* External collaboration
* Support PDF as Offline Output in local build

Open Localization
* can create high prio/normal prio/special HO based on metadata (ms.topic) 
* HO & HB repository cleanup or archiving contents to a different branch 
* To be able to create a separated HO based on content priority (HT/MT)

DocFx
* REST API support 

## Sprint 96
No updates affecting partners.
## Sprint 95
Open Localization
* Support for XLIFF 2.0 
 
Start features in this sprint:
•	Feature 467842:[OL] bi-lingual I can view en-us and translated content on localized page
•	Feature 445899:[OL]To be able to create a separated HO based on content priority (HT/MT)
•	User Story 467231: [OL] To be able to setup publishing config as soon as locale is specified - plan to finish in S96

DocFx
* Managed reference content (C# + VB) publish through docfx-OP pipeline 

## Sprint 94
* [Support Azure markdown extensions - at CAPS level](../partnerdocs/GFM.md)
* [Editable SEO meta in content MD file](../partnerdocs/metadata.md)
* [REST API Support via Swagger](../partnerdocs/REST_API_Support.md)
* [APIScan for un-managed reference](../partnerdocs/APIScan.md)
* [Publish to TechNet](../partnerdocs/publishedpages.md) 
* [Page level redirection from OP](../partnerdocs/OPredirection.md) 
* [De-couple engineering-only config files from existing configuration model](../partnerdocs/local-build-and-preview.md)
* [External code snippets](../partnerdocs/codesnippets.md)

## Sprint 93
No updates affecting partners.

## Sprint 92
* [Display content author, last updated time and contributors](../partnerdocs/publishedpages.md)
* [Publishing environment updates](../partnerdocs/publish.md)
* Support VS.com
* [Support index page for folders](../partnerdocs/URL-management.md)
* Support customized 404 page for each DocSet
* [Code syntax highlighting](../partnerdocs/codesnippets.md)
* Support multiple versions of handoff and handback

## Sprint 91
* [Metadata support](../partnerdocs/metadata.md)
* Offline format generation - HTML
* Support public repo for external collaboration while private (or public) repo for internal staging

Localization
* Auto E2E workflow support for HO/HB/Loc publish in GIT repo
* Support auto sync between en-us and localized repo
* MD->XLIFF transformer, supporting all the extensions
* HO and HB reporting and file tracking in GitHub
