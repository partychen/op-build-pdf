# Onboarding to Open Publishing and docs.microsoft.com

Thank you for your interest in onboarding to OPS (Open Publishing Services) and docs.microsoft.com. Please be aware of the different guidelines depending on the onboarding cases. Each release should have an onboarding PM in APEX. We provide contacts below in case you have any questions or issues. 

3 ways to onboard:
1. Create brand new content
2. Move a project from a different system (such as CAPS, DxStudio, etc.)
3. Move a project from OPS MSDN/TN to OPS docs.microsoft.com
## Creating a brand new project or moving from a different system
Contacts: Sandra Aldana and Jennifer Mashkowski.

1. We have built a tick-tock plan for both content owners and APEX onboarding PM to follow. [Create a copy of the tick-tock plan](https://microsoft.sharepoint.com/teams/STBCSI/e/CE/_layouts/OneNote.aspx?id=%2Fteams%2FSTBCSI%2Fe%2FCE%2FCSI%20REL%2FCSI%20Release%20Tick%20Tock&wd=target%28Tick-Tock%20Overview.one%7CCCAFE2C7-977A-4663-8611-342DBB04A631%2FTick-Tock%20Checklist%20%28Template%5C%29%7C77AD99BC-658F-4544-B96F-B1249DA48F1C%2F%29).

2. Add  your release to our release tracking. All content onboarding to OPS is tracked in VSTS now. For consistency, we are keeping English and loc releases separated even if they release on the same date. Make sure you maintain the release information up to date until you go live.

    * For English release, add your release using the [following template](https://mseng.visualstudio.com/CSI/Onboarding/_workItems?_a=new&witd=Feature&templateId=5ce006d4-87bd-4dff-adb4-b710009dae4c). Please read the instructions in the **Release Notes section**.
    * For Loc releases, add your release using the [following template](https://mseng.visualstudio.com/CSI/Onboarding/_workItems?_a=new&witd=Feature&templateId=5fca7f82-7976-49c0-96a5-416a0cc4941a). Please read the instructions in the **Release Notes section**.
    * You can see all the releases via this [VSTS query](https://mseng.visualstudio.com/CSI/Onboarding/_queries?id=3c45d380-9fe3-4fd3-90e9-6a994e1b703a&_a=query).

> [!IMPORTANT]
> To better manage the repos and the sitemaps per repo we are asking teams to not create repos for just couple pages.  To utilize our repo and sitemap file capacity please create repo at the minimum of 25 pages unless there is a strong business justification.

## Moving content from MSDN/TechNet OPS to docs
Contact: Sandra Aldana

1. We have built a tick-tock plan for both content owners and APEX onboarding PM to follow. [Create a copy of the tick-tock plan](https://microsoft.sharepoint.com/teams/STBCSI/e/CE/_layouts/OneNote.aspx?id=%2Fteams%2FSTBCSI%2Fe%2FCE%2FCSI%20REL%2FCSI%20Release%20Tick%20Tock&wd=target%28Tick-Tock%20Template.one%7CCCAFE2C7-977A-4663-8611-342DBB04A631%2FTick-Tock%20Checklist%20%28Template%5C%29%20-%20From%20MSDN%5C%2FTN%5C%2FVS%7C67DC3619-B19E-4A19-8562-BB4F7AE4A5D6%2F%29).

2. Add  your release to our release tracking. All content onboarding to OPS is tracked in VSTS now. For consistency, we are keeping English and loc releases separated even if they release on the same date. Make sure you maintain the release information up to date until you go live.
    * For English release, add your release using the [following template](https://mseng.visualstudio.com/CSI/Onboarding/_workItems?_a=new&witd=Feature&templateId=5ce006d4-87bd-4dff-adb4-b710009dae4c). Please read the instructions in the **Release Notes section**.
    * For Loc releases, add your release using the [following template](https://mseng.visualstudio.com/CSI/Onboarding/_workItems?_a=new&witd=Feature&templateId=5fca7f82-7976-49c0-96a5-416a0cc4941a). Please read the instructions in the **Release Notes section**.
    * You can see all the releases via this [VSTS query](https://mseng.visualstudio.com/CSI/Onboarding/_queries?id=3c45d380-9fe3-4fd3-90e9-6a994e1b703a&_a=query).


## Onboarding tracking staus
The onboarding PMs will be updating the contents and status of the onboarding work items in TFS. We will be using the following Statuses:
* *Proposed*: When the release item is created
* *On deck*: If the onboarding PM agrees it should be assigned to him but there is some investigation to do or the Go live date (Milestone) is set to TBD.
* *Committed*: If all the parties (content team and APEX) have agreed that the content can onboard to OPS-Docs.
* *In progress*: The project is already in place, with a tick-tock, etc. 
* *Cut*: The project did not fit the requirements to be in OPS-Docs.
* *Completed*: The content has gone live.

## Onboarding tracking tags
The onboarding PMs will be adding tags to the onboarding feature item in TFS. Tags used are:
* **new** - If this is brand new onboarding and not migration from technet/MSDN or any other site
* **technet-migration** - If the portfolio you are migrating is from Technet
* **msdn-migration** – If the portfolio you are migrating is from MSDN
* **vscom-migration** - If the portfolio you are migrating is from visualstudio.com
* **developer-migration** - If the portfolio you are migrating is from developer.com
* **dev.office-migration** - If the portfolio you are migrating is from dev.office.com
* **archive** - An archive experience on the Docs site, separate from the main site, but using the same publishing process (OPS). At this time, the plan is for this content to be excluded from external search. The archive site is scheduled for deployment in Q1.The new suite of migration tools built by APEX (XHMTL extraction and Pandoc conversion to .md format) will provide OPS-ready sources.
* **remove** - Content in MTPS is not migrated to a new endpoint, although the new extractor tool will store the XHTML source from the MTPS database for later use if necessary.
* **retire** - Content is paved over in the MTPS database and placed into PDF files on the Microsoft Download Center. Content within the PDFs is not externally searchable, although the DLC details pages pointing to the PDFs are crawled and indexed. This process is available for use now.
* **blocked** – If the onboarding is blocked due to pending feature or business decision.
* **other** – This tag is used if none of the above listed tags fit. We will visit portfolios with this tag every triage meeting to determine the right approach. 

