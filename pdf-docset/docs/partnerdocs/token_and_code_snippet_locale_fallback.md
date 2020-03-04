# Token and Code snippet locale fallback

Token and code snippet locale fallback is a general request from localization team.

## Fallback cases
- Token fallback case:  
  Because of OL workflow that user can localize the content partially and handback partially, most time some tokens don't handback together with the content. That will cause build errors as OPS regards the article that references the token as imcomplete and stop publishing them.
- Code snippet locale fallback case:  
  Most code snippets don't have difference between localized repositories and en-us repository, so under most cases, user won't handoff the code snippets in OL workflow. That will also cause code snippets missing error during localized repository build.

Token and Code snippets locale fallback is created to resolve those kinds of issues.

## How does locale fallback work
Locale fallback can work as long as user add fallback repository as CRR in .openpublishing.publish.config file.  
For example  
en-us repository: https://github.com/Microsoft/openpublishing-docs  
zh-cn repository: https://github.com/Microsoft/openpbulishing-docs.zh-cn  
Locale fallback work machanism is that clone both repository when building zh-cn repository. Once a token or code snippet can't be found under zh-cn folder, it will search the en-us repository as a fallback folder.

## How to configure the fallback repository
Fallback repository implementation based on [CRR](cross_repository_reference.md) feature. Once user add a CRR with `path_to_root` match the style `_repo-{locale}`, that CRR will be recognized as a fallback folder.  
Sample configuration:  
```json
{
    "dependent_repositories": [
        {
            "path_to_root": "_repo.en-us",
            "url": "https://github.com/Microsoft/openpbulishing-docs",
            "branch": "master",
            "branch_mapping": {}
        }
    ]
}
```

> [!NOTE]
> Currently, the fallback function will enable once you add the fallback CRR. No more other flag to turn off that.  

> [!IMPORTANT]
> As mentioned above, the fallback works by cloning fallback repository, so the performance with enable this will be worse than before. 