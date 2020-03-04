# Provisioning updates 

There are some provisioning updates we need to do during FY17Q2 and FY17Q3 to improve customer's experience. For better both internal and external user experience, we will move all OPS GitHub repos to Microsoft docs organization. Thus, this page contains changes we need to make to comply with the new organization as well as additional changes we would need to do to solve some of the customers' problems we are seeing today that will save both customer and engineering time. 

## Potential customers
* Content owners
* OPS Engineering Teams

## Goals
* Help with better solution for provisioning repos
* Make provisioning more robust by addressing common problems

## Non goals
* Provide support for repo administration such as permission granting or team creation.

## Roadmap
S110- ???

## User scenarios
### English docset provisioning
User goes to the https://OPS portal and provisions a new docset. When the user is finished provisioning, he gets the following:
* If the repo does not exist, OPS creates the repo for the user. 
* User gets admin access to the repo.
* Docset is connected to OPS build. 
* OPS configuration files are added. 
* OPS will add English License.md file with link to Creative Commons license.
* CLA is automatically enabled for public repos.

***User then will have to:***
* Go to the OSPO portal or GitHub and administer their repo from there: create new teams, grant permissions to the repo to teams or other users, etc.

### Localization docset provisioning
User goes to the portal, selects the English docset, and adds new locales to provision the docset via the [OPS portal](https://OPS). When the user is finished provisioning, he gets the following:
* If the repos did not exist, OPS creates the repo for the user. 
* User gets admin access to the repos.
* Docsets are connected to OPS build. 
* OPS configuration files are added. 
* OPS will add English License.md file with link to Creative Commons license.
* CLA is automatically enabled for public repos.

***User then will have to:***
* Go to the OSPO portal or GitHub and administer their repos from there: create new teams, grant permissions to the repo to teams or other users, etc.

## Engineering changes 

### Related to moving to Microsoft docs organization

#### Service account
We need to use a service account to create the repos via OSPO API. The service account will be also used to a. Clone the repo for build; b. Set PR status and add comment. Otherwise, we face the following issues 
* We cannot provision the repo via OSPO API as only a small amount of service accounts is advised to be used. 
* The account is sued 
* If the user is no longer an admin in the repo, PRs might start failing.
* Using a user's account can be seen as spoofing.

Thus, we agreed to use a service account for provisioning as follows:
•English repos - OPSBuild
•Loc repos - OLProd (no change, already in place)

#### Access for service accounts
* Service accounts and teams need access to the repo by default. We should that during provisioning.
    * GitHub
        * OPSBuild – Write - Service account for cloning the repos for build and Set PR status and add comment.
        * [OPS_Admin](https://github.com/orgs/MicrosoftDocs/teams/ops_admin) – Admin
        * [VSC-Eng-Team](https://github.com/orgs/MicrosoftDocs/teams/vsc-eng-team) – Read
        * [OPS_Serviceaccounts](https://github.com/orgs/MicrosoftDocs/teams/ops_serviceaccounts) - Read. The following two accounts are part of this team: 
         * [UDMSa1](https://github.com/UDMSa1) - Read
         * [olprod](https://github.com/olprod) – Read
    * VSTS
        * OPSBuild – Write - Service account for cloning the repos for build and Set PR status and add comment.
        * Olprod – Read
        * Openloc – Read
        * OPS_Admin (DG, no GitHub team) – Admin
        * vscsdses - Read
        * OPS will add License file (LCA needs to provide the file. It will be in English for all locales)
        
### Unrelated to moving to the Microsoft docs organization
These are provisioning changes we should be doing, no necessarily related to the moving to OPS organization
* We should not add TOC and index.md in live branch. 
    * This causes issues for both English and loc when we set up the GotoLive flag on but they have not committed the content to live branch. This is particularly important for localization when they do not do simultaneous ship: the index file gets published. 
* Pull request for protected branches
    * When the branches are protected, provisioning fails. Instead, we should send a PR for the user to approve with a comment indicating that once the PR is approved, they can go to the portal and do the provisioning again. As the files are already in the repo, provisioning should work then.
* Master branch is hardcoded
    * Some teams do not use *master* branch name as their working branch, but have a different branch name, such as *staging*. Right now, OPS always provisions in the master and live branches. We should provision in the *live* and ***default branch*** in GitHub or VSTS.
* As a short-term solution, we need to remove the restriction of having users be part of OpMember to add a new locale for a docset that is live. 
* Updating API for provisioning scenario: "When user creates a new docset, we will check whether the same depot exists in DHS, if so, the request will be rejected. That means when after you create a docset, no one else can create the same docset (even with a
different locale) unless you do a deprovision first.  Add a new locale will go through duplicate repo scenario so doesn’t have this restriction. And after we add this check, we can remove the restriction of requiring user to be OP admin."
* Remove build_output_folder from .openpublishing.publish.config.json for provisioning. It is confusing for users as they think this is the docset folder. 
* If a user is in VSO, they can change the publish live flag so long they are admins in the repo. We need to add a second layer of security. I added OPS_Admin distribution group, we should use that one for our restriction. 

* As we move forward with the PDF integration, one key part is to ensure that every repo has an actual PDF build associated with it. Per earlier conversations with Xiaokai, we’ll need to add the following to bind both master and live branch builds to PDF kick-offs ***when the user chooses docs as an output***:
 
   "branch_target_mapping": {
        "master": ["Publish", "Pdf"],
        "live": ["Publish", "Pdf"]
    },
 
   In addition to the above, we’ll also need to tell docs to show a Download PDF link on the site:
   
   "need_generate_pdf_url_template": true 
