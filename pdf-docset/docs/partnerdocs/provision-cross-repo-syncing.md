# Provision cross-repo syncing

---
author: herohua
---

> [!NOTE]
> Currently, we don't support provision of cross-repo syncing in [OPS self-service portal](https://OPS). Please contact your onboarding PM AND Sandra Aldana if you want to use this feature.

## Recommendation
We recommend the following syncing for the private and public scenario:
1. private repo, live branch -> public repo, live branch
2. public repo, live branch  -> private repo, master branch

## Provision data syncing between two GitHub repos

> [!NOTE]
> Currently, we don't support syncing data between two VSO repos, or from GitHub repo to VSO repo, or vice-versa.

Suppose we'd like to setup a cross-repo syncing relationship, a.k.a. a syncing pair between repo A (branch live) and repo B (branch live).
Following information is needed for provisioning.

| Item | Meaning | Required? | Example |
| ---- | ------- | --------- | ------- |
| repo A's URL | The repo you are syncing from | Yes | `https://github.com/MicrosoftDocsVirtualization-Documentation-Private` |
| repo A's syncing branch | The branch you are syncing from | Yes | `live` |
| repo A's working branch | Working branch is managed by OPS and used for resolving conflicts in PRs. | No. If not provided, OPS will append `-sync-work` to syncing branch as the name for working branch.  | `live-sync-work` |
| repo B's URL | The repo you are syncing to | Yes | `https://github.com/MicrosoftDocs/Virtualization-Documentation` |
| repo B's syncing branch | The branch you are syncing to | Yes | `live` |
| repo B's working branch | Working branch is managed by OPS and used for resolving conflicts in PRs. | No. If not provided, OPS will append `-sync-work` to syncing branch as the name for working branch.  | `live-sync-work` |
| whether to require a PR opened when syncing from repo A to repo B | <ul><li>If `false`, changes in repo A's syncing branch will be pushed into repo B's syncing branch automatically if there is no conflict.</li><li>If `true`, OPS will open a PR for users to confirm the merge.</li><li>In either case, if there is conflict, a PR will be opened for users to resolve and resume syncing.</li></ul> | Yes | `false` |
| whether to require a PR opened when syncing from repo B to repo A | <ul><li>If `false`, changes in repo A's syncing branch will be pushed into repo B's syncing branch automatically if there is no conflict.</li><li>If `true`, OPS will open a PR for users to confirm the merge.</li><li>In either case, if there is conflict, a PR will be opened for users to resolve and resume syncing.</li></ul> | Yes | `true` |
| user id | The user should have **Admin** permission in both repos. OPS will use the credential of the user to create webhooks on both repos. | Yes | `hexiaokai` |

> [!NOTE]
> It is recommended that users grant [`openpublishbuild`](https://github.com/openpublishbuild) account **Write** permission in both repos.
> This account will be used to open PRs during syncing.

> [!TIP]
> If you would like to sync from repo A to B and from B to A, you need to provide two sets of configurations.

> [!NOTE]
> Syncing from one repo to another will happen on the committed content on the branch. So if there are any pending Pull Requests into Repo A source branch, that content will not be merged into Repo B target branch. You will still have to manually accept any pull requests that are coming to your branches before the syncing can happen. 

## Provision user info syncing from a GitHub repo
OPS supports syncing of user info from a GitHub repo into global user profile cache in backend storage. After the user info is synced, VSO repo can also resolve author and contributor information during publishing if `resolve_user_profile_using_github` in [publishing config](publish-configuration.md) is set to `True`.

The information required to provision an user info syncing is: 
 - GitHub repo's URL
 - GitHub repo's syncing branch
 - VSO repo's URL
 - user id that has **Admin** permission in the GitHub repo.

## Technical details behind the syncing
See techinical design document [here](syncing-repos.md).
