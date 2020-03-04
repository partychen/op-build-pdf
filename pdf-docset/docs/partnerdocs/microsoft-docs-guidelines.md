# Microsoft docs GitHub organization Guidelines
All the repos for a given release should be in the same organization. So please do not create English repo in one organization and localized repos in another. 

### Private repos
With the current plan that we have (Aluminum), we can host up to 1,500 private repos. This might look like a lot, but considering that we need one repo per locale, the amount increase very quickly. So please be mindful with the amount of private repos you create.

### Private repos guidelines

* WDG will use VSTS for private repos and GitHub for public repos.
* ASG might use private repos in VSTS or GitHub and public repos in GitHub.
* C+E will use VSTS for private repos for VSTS projects. For rest of the projects, they will use private and public repos in GitHub.

## Microsoft docs organization team policies
We do not recommend creating teams as the standard practice – rather people should use existing broad teams. 

This kind of org movement is a great time to do a “cleanse” of the team memberships, rethink how they are fitting together, and then asking people to join the appropriate teams.
 
I believe even a single team per repo is much too granular an approach in the modern engineering systems world. Give people broad access and approve a few folks who have admin.
 
If you look at 1ES and other engineering systems inside the company, you typically give an entire organization or the entire company read access – so that’s a standard “Everyone” team with read access. Many of our engineering systems then give a majority of folks write access, but in the GitHub world, you really don’t need that at all.
 
So for the entire Microsoft Docs project it seems like you will want to just use a few teams and trust people to do the right thing:
	• Everyone team – read access – this team already exists
	• Microsoft Docs Approvers – write access – call it what you like, I think that makes it clear, recommend you create this for people who should have permission to approve pull requests and perform direct writes. [Sandra] We might want to have one per organization.
	• Microsoft Docs Admins – admin access – recommend you create this and use it for all of your repos; folks like Sandra and her trusted “admins” should be in this team, able to help when people have administrative needs
 
This way you don’t need to create a new team for every repo – that would be a nightmare to manage in my opinion!
 
If I look at the Azure org on GitHub, it’s pretty common to see something like an “Everyone” team in use with read access, then a team like “Service Fabric Write” – full of people on the Service Fabric team who are trusted to directly write and also approve pull requests – let’s say this is like 30% of the team – and then a “Service Fabric Admins” team with about 5 people in it who have admin on the repos.

## License and readme guidelines
The Open Source CELA team has provided some files that each repo should have. It is the repo owner's responsibility that those files are in the repo, specially when the repo is public and exposed to customers outside Microsoft.

1. LICENSE
2. LICENSE-CODE
3. ThirdPartyNotices
4. README-template.md

These files can be found at the root of [this repo](https://github.com/Microsoft/openpublishing-docs/).

> [!IMPORTANT]
> The LICENSE, LICENSE-CODE files and ThirdPartyNotices are put in the repo unchanged. Content owners are not supposed to convert the plain text to markdown or any other form or include additional text.  That makes interpretation harder and foils autodetection algorithms. These files are not to be localized either.
> The README-template.md text should be copied and pasted into the repo’s README.md, in some consistent location (likely at the top)

Additionally, there will `not` be validation during build for these files, so if you delete or update the files, OPS will not notify you. 
