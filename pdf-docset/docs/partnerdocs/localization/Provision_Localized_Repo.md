# Provisioning localized docsets

Provisioning localized docsets has three parts:
1. Creating the localized repos if they do not exist already 
2. Connecting the localized docsets to Open Publishing Build System.
3. Connecting the localized repos to Open Localization and create the handoff and hand back repos.

## 1 & 2: Creating the localized repos 
Owner: Localization PM in content partner team.
Pre-requisites: English repo is created, docset is not live, Localization PM has read-only access to English repo.

Steps:
1. Go to the [OPS Portal](http://OPS).
2. Sign into the portal with either your GitHub or VSTS credentials.
3. On the left navigation, search for the docset name you would like to add locales to.
4. Select the docset.
5. Click on "Manage Localized Repos"
6. Add the additional locales and select "Save".

If the repos do not exist, OPS will create them for you. 

> [!IMPORTANT]
> Do not create the repos in Microsoft organization. If your team has an organization, create them there, otherwise, create them in "Microsoft docs" organization.

If English content is live, then you can still can create the repos, but cannot connect them to OPS. To connect them to OPS:

Create a [Go live ticket](../golive.md) ticket for our team. Makesure we have the right [permissions](../repo-creation-config.md#repo-perms) to your repos.

>[!NOTE]
> If English content is live and you commmit any content to live branch, the content will automatically go live.


## 2. Connecting the localized repos to Open Localization and create the handoff and hand back repos
Owner: Localization PM in content partner team and VSC engineer.

Pre-requisites: Localized repos are connected to OPS
`Please enter your request 3 days in advance.`

**Partner** to create a request under [SiteHelp portal](http://aka.ms/sitehelp).  Include:
- **Business proposition** - Business justification as of why the request is important. 
- **Project name:**
- **URL to English repo:**
- **English-repo branches to create handoffs from:**
- **Date for when you want to start loc:**
- **Locales** - List the locales that you need support.
- **Permissions**
    * GitHub
        * Make sure that "olprod" account has read-only access to English repo.
	    * Make sure https://github.com/orgs/Microsoft/teams/vsc-eng-team team has read-only access to the English repo.
    * VSTS
        * Give READ access to "openloc@microsoft.com" and "olprod@microsoft.com" account to English repo.
        * Alias (GitHub or VSTS) of users who need access to the localized repos, handoff and hand back repos. Create a group to grant permissions instead of individually.

APEX will 
1. Configure Open Localization Service. 
4. Grant access to groups specified by the IPM team to handoff and hand back repos.

##<a name="MatchENandLocDocset"> </a>Keeping configuration files in sync between languages 
OPS now has a plug in that allows you to keep the configuration in the localized repos matching the English ones or between the localized repos 

To install the plug in:
1. Go to [OPS portal](https://OPS).
2. Click on ***Plug ins***. The plug in you want is ***ConfigManager*. 
3. Click on ***Install.***

To use the plug in once installed:
1. Go to [OPS portal](https://OPS).
2. Go to the docset you would like to do the syncing.
3. You will see the plug in options at the bottom of the page, under ***Merge configurations on master branch from specific locale***.
4. Select the locale you would like to do the merge from.
5. Select the locales you would like to do the merge to.
6. The table will show you the number of configuration files that are different. You can click on the link to see the difference in GitHub or VSTS.
7. Click on ***Merge with pushing directly***.

####<a name="RemovingLocRepos"> </a>Removing loc repos 
You can remove a localized repo from OPS. Steps:
1. Go to the [OPS Portal](http://OPS).
2. Sign into the portal with either your GitHub or VSTS credentials.
3. On the left navigation, search for the docset name you would like to remove locales from.
4. Select the docset.
5. Click on the settings button and click on "Manage Localized Repos".
6. Remove the locale(s) from the "Locales" list. 
7. Click on "Save".

