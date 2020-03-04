# OPS provisioning - Keeping English and loc docsets in sync (decommissioned)
> [!NOTE]
> After talking to Sonja and Albina, implementing this feature will bring more problems than it will solve. Thus, we are not going to implement this.


## Overview
Localized repos are often dependent on English repos. It is not infrequent that English creates new docsets and localized are off sync. That means that even localization team localizes the content, the localized content will not be published and default to English. There are some occasions though where the localized team does not need to localize a particular docset for either all locales or some of them.

With the new portal and self-provisioning, we need to make this options available for our customers. 

## Goals
1. Allow users to ensure English and localized docsets are always in sync (default experience).
2. Allow users to decide whether a docset should be localized and for which locales.

## Non-goals
Remove locales from a docset once the docset is provisioned/configured. All the locales need to be removed at the same time.

## Scenarios
### 1. User creates a new docset in a repo for the first time
User wants to create a new docset in a brand new repo. During provisioning steps, OPS shows English as a default locale. User decides to add other locales in addition to English or provision English only. At the end of provisioning, for all locales user selected, the corresponding repos are created (if the repos do not exist) and the docset is provisioned.

### 2. User creates a new docset in a repo that already has one or more docsets assigned to the same locale set
User wants to create a new docset in a repo that already has one or more docsets provisioned to a matching locale list. During provisioning steps, OPS shows all the locales that the other docsets in the repo are configured. At this point, user can decide to edit the locale list. At the end of provisioning, the docset is provisioned for all locales selected.

### 3. User creates a new docset in a repo that already has multiple docsets with different locales assigned
User wants to create a new docset in a repo that already has multiple docsets provisioned to different locales. During provisioning steps, OPS shows as the default locale list the matching list of locales among all the docsets in the repo. At this point, user can decide to edit the locale list to add or remove locales. At the end of provisioning, the docset is provisioned for all locales selected.

### 4. User edits a new docset to add new locales (added for completeness here)  
At any time, user can select a repo and add new locales to a docset. So user is not limited to do this during the initial step.

## Roadmap
S105 - This functionality is signed off by parner and engineering
S106 - This functionality is completed by VCS

## Competitive Landscape N/A.
N/A

## Basic Design
We will follow the design already in the portal.
