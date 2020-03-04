---
# Mandatory fields. See more on aka.ms/skyeye/meta.
title: OpenLocalization high level overview
description: Describes the high-level functionality of OpenLoc, a service of the Open Publishing System
services: service-name-with-dashes-AZURE-ONLY 
keywords: Don�t add or edit keywords without consulting your SEO champ.
author: {author}
ms.author: Sonja Saltzman
ms.date: 06/06/2017
ms.topic: article-type-from-white-list
# Use only one of the following. Use ms.service for services, ms.prod for on-prem. Remove the # before the relevant field.
# ms.service: service-name-from-white-list
# ms.prod: product-name-from-white-list

# Optional fields. Don't forget to remove # if you need a field.
# ms.custom: can-be-multiple-comma-separated
# ms.devlang:devlang-from-white-list
# ms.suite: 
# ms.tgt_pltfrm:
# ms.reviewer:
# manager: MSFT-alias-manager-or-PM-counterpart
---

# OpenLocalization

OpenLocalization (also called 'OpenLoc' or 'OL') is a service of the Open Publishing System ('OPS'), which was developed to support the localization workflow.
OL has following high-level features:
- monitors en-US GitHub or VSOgit repositories as specified by the localization PM 
- for any new/updated en-US source files, OL creates loc files in xliff format for each locale specified by the localization PM
- xliff files are placed in to a Handoff repository
- xliff files are handed off to the localization supplier, localized, and handed back to OpenLoc
- OL transforms the localized xliff files into localized markdown files and commits them to the target locale repositories
- OL also monitors any file movements (e.g. moves from folderA to folderB) as well as file deletions, and performs the same action on the loc repos, keeping the localized content in sync with en-US

You will find detail explanations to the individual functionality in other topics.

## Implementations of OL

The first version of OL is basically "standalone" mode. Users using the standalone mode need to either manually handoff/handback loc xliff files from the HO repo and to the HB repo, or build their own automation. The standalone version of OL has a handoff repo, handback repo, and localization configuration file, as well as a localization status report.

The newer implementation of OL is a tight integration with iCMS, the ASG team's content localization file management system.  OpenLoc serves as a backend Content Management System (CMS) for iCMS. 
For more information, please see the [iCMS User's Guide](https://microsoft.sharepoint.com/teams/Office_GSX/_layouts/15/WopiFrame2.aspx?sourcedoc={bdf80bb4-8439-4612-9872-ce238aa7924e}&action=edit&wd=target%28User%20Guides%2Eone%7C9CEB3E07%2DF5EB%2D45CF%2D95A5%2D8D812AB47432%2FOpenLoc%20and%20iCMS%7C80A1F074%2D6E56%2D4F4A%2DA70A%2DAB12B3120947%2F%29) and all pages below this section.
The iCMS-integrated version of OL no longer requires handoff repo, handback repo, localization configuration file, or localization status report. This functionality has been replaced by the iCMS UI.

For more information, please contact Sonjas@microsoft.com 
