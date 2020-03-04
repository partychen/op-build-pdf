# Creating and configuring the the GIT repos
It is the content owner's responsibility to create and configure the GIT repos and provide the right permissions to the users to access them. 
A GIT repo is either GitHub or Visual Studio Team Services (VSTS). See [Choose between VSTS Git or GitHub](VSTSGit-GitHub.md) before proceeding.

Note that you can have 3 scenarios:
1. Private repo only
2. Public repo only
3. Private and public repo. In this case, the private repos is configured for OPS build and publishing while the public repo is only used for external contributions. 


## 2. Creating your OPS repo
We recommend that you create the public repos in the GitHub MicrosoftDocs Organization. That way, all Microsoft repos are together in a single GitHub organization. Also you can benefit of all the advantages the organizaiton provides, including enabling Contribution License Agreement (CLA) automation. If so, please first join the [Microsoft docs GitHub organization](https://www.1eswiki.com/wiki/How_to_Join_the_Microsoft_GitHub_Organization).

### <a id="ConnectENDocset"> </a>2.1 Creating the English repos
> [!NOTE]
> You can create and connect the repos to Open Publishing can be done via the OPS self-service portal. You can look at the [OPS Portal](../OPSPortal.md) page to see all the scenarios that are supported. 

In order to connect the repo to Open Publishing, you need to create a docset. A docset is a group of documents that share the same configuration like template, base URL, etc.

In the portal, select ***New Docset*** on the top left corner. Follow the steps of the wizard. 

You will get a notification when the repo is created with additional information about the [Contribution License Agreement (CLA) automation](https://www.1eswiki.com/wiki/Automating_Contribution_License_Agreements), teams added to the repo, and such. 

The repo will be created with initial files inclufing legal notices and a reference to the code of conduct (Sprint 115). 

## 3. Adding and provisioning localized repos
[Add and connect localized docsets to OPS based on English settings](localization/Provision_Localized_Repo.md).

## <a name="repo-perms"></a>4. Setting up permissions to the GIT repo
Content owner is responsible for granting and maintaining the repo permissions by leveraging GitHub permission system. The owner will need to give the appropriate users the right permissions. Our recommendation is you create teams, then add users to that teams to give them the appropriate permissions. 

The following account should also have access to your repo for good support prior going live and post-live.
* GitHub (Microsoft docs organization) 
    * [OPS_Admin](https://github.com/orgs/MicrosoftDocs/teams/ops_admin) – Admin - Help set up the [Goto live](golive.md) flag. 
    * [VSC-Eng-Team](https://github.com/orgs/MicrosoftDocs/teams/vsc-eng-team) – Read - Troubleshoot your LSIs.  
    * [OPS_ServiceAccounts](https://github.com/orgs/MicrosoftDocs/teams/ops_serviceaccounts) - Read - OPS service accounts such as [Open Localization](https://github.com/orgs/MicrosoftDocs/teams/ops_serviceaccounts), Skyeye accounts: [UDMSa1](https://github.com/UDMSa1) & [skyeyedev1](https://github.com/skyeyedev1), and [testing account](https://github.com/apextest).

> [!IMPORTANT]
> * If you are outside the Microsoft docs organization, then you need to add the individuals from those teams above to your repo or allow our team to create those teams in your organiation.
  
* VSTS  
    * Olprod – Read  
    * Openloc – Read  
    * OPS_Admin – Admin  

To learn more about repo permissions in GitHub, please see the [Repository permission levels for an organization page](https://help.github.com/articles/repository-permission-levels-for-an-organization/). 

## 5. Configuring the repos
Content teams need to so some configuration in their repos after creation.


### 5.1. Initial repo configuration

#### 5.1.1 Examples of repo structure
The following is a repo structure with one docset.
```
/
|- .gitignore
|- README.md
|- docset/
|  |- a.md
|  |- b.md
|  \- TOC.md
```

The following is a repo structure with multiple docsets and independent TOCs.
```
/
|- .gitignore
|- README.md
|- docset1/
|  |- a.md
|  |- b.md
|  \- TOC1.md
\- docset2/
   |- c.md
   \- d.md
|  \- TOC2.md
```

The following is a repo structure with multiple docsets and a single TOC.
```
/
/
|- .gitignore
|- README.md
|- docset1/
|  |- a.md
|  \- b.md
\- docset2/
   |- c.md
   \- d.md
\- TOC.md
```

## 6. Branches
In open publishing, we use GIT branches to maintain different copies of the same content. Same topic in different branches will be published to different urls of rendering sites. This could be used in several scenarios:
1. Stage/promote. User can use one branch as staging branch and merge it to a live branch as a promote operation.
2. Private working branch. User can create his own branch to save files that are still under writing, and merge it to common branch when he is ready. Files in private branch can still be validated/previewed by open publishing.

### 6.1 Live Branch
Among all branches, there is only one branch that is exposed to external users, and other staging/working branches are only used by writers for internal testing. This branch is called "live" branch. Content in live branch will be published to the live site. Content in other branches will still be published, but only to stage.
