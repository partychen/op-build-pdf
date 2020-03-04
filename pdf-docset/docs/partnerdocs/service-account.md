# Setting a service account for build and PR validations

By default, OPS has been used the account of the person who created a repo for build and PR validation. This brings some problems:
* It is confusing as contributors might think that person is going to answer any questions they might have. 
* The person for which account is being used, gets notifications for each PR or push to the repo, making it hard for them to distinguish which notifications are noise and which ones they have to act upon.
* There is a call limit of how many calls an account can be made in an hour to the GitHub API (xxxxxxx per hour (check with Feng)).

Thus, we have implemented the ability to use service accounts for both PR and validations that will solve all the problems above. 

If your repo is in MicrosoftDocs organization, by default, we will enable that any repo created via the OPS Portal, will have OPS service accounts activated. Alternatively, you can use your own bot. Likewise, if you are in a different organization, you might set up your own as self-service. 

1. In OPS portal, go to repo settings
2. 