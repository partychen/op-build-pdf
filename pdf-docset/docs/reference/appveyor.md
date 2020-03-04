# AppVeyor and Reference Content  

* Appveyor is an app that we, Docs, use to automate and validate some reference-related processes. 
* Every reference project needs its own AppVeyor project.


## How to create a reference appveyor project

### Requirements:

1. You have admin permissions in AppVeyor.
2. You already have a repo in GITHUB (not VSTS) where you plan to process the documentation, this is not the repo where the code is hosted. Permissions from Github are already available.
3. You already have everything configured on the documentation repo, including an appveyor.yml file.
4. You added the [VSC-Service-Account](https://github.com/VSC-Service-Account) alias as admin to the repo that has the appVeyor file.

### Steps to Create a new appveyor project

1. Go to https://ci.appveyor.com/login and login.
2. Click the "New Project" link.
3. Select Github.
4. Look for the name of the repo that will host the documentation (not the code) and click "Add".
5. Trigger a new build manually and if everything is configured properly it should pass.

### Build Settings
if you want your build to run every 6 hours, add this under the build schedule box: 0 */6 * * *

## Related content
[Setup a reference repo from zero, appveyor steps included](https://opsdocs.azurewebsites.net/en-us/opsdocs/reference/howto-onboard-reference-project?branch=master#create-a-doc-repo-from-zero)
