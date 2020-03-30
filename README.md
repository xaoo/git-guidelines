# **GitOps Documentation**
## <font color='green'>**A comprehensive mindset for any contributors.**</font>
   > 1. Remember the [guidelines](#guidelines)!
   > 2. Understand and use repository [workflow](#gitworkflow)!
   > 3. Never push branch without a [naming convention](#naming-conventions) in place!
   > 4. Understand and keep a [branching strategy](#branching-strategy)
   > 5. Use a [pull request process](#prprocess) before submitting new code!
   > 6. If you are part of Release Management, use [semantic versioning](#semver) for your components!
   > 7. Track a [changelog](#changelog) file for your new project
   > 8. Do not forget to add in your code, wherever is possible, [COPYRIGHT] information!
   > 9. [Git Cheatsheets], start working with GIT, a comprehensive command list, made easy to understand!
   > 10. [More Readings](#readings)
   > 11. [Authors](#authors)

# <a name="guidelines"></a> Guidelines
When contributing to any any repository, please first discuss the change you wish to make via issue, email, 
or any other method with the owners of any repository before making a change.

Please note we have a code of conduct, please follow it in all your interactions with the project.

1. **Make, clean, single-purpose and logical commits**
   > it means that you need to commit after every single-purpose modification
   > 
   > this is a good way of going back to you changes, without spending more time to actual 
   >
   > this is a good way of going back to you changes, without spending more time to actual 
   >
   > find local bugs, missing files, lost code lines, etc.
2. **Write meaningful commit messages**
   > <font color='red'>**Bad**</font>:
   >
   > > Author | Commit | Message | Commit date
   > > ------ | ------ | ------- | -----------
   > > John, Doe |886117771d8 | test | 1 hour ago
   > > John, Doe |cxb9a2443a0 | test1 | 2 hours ago
   > > John, Doe |13x0360b4b7 | test100 | 2 hours ago
   > > John, Doe |08b7f2fx462 | doamne ajuta | 2 hours ago
   > > John, Doe |x8b7f2f6462 | sper ca merge | 2 hours ago
   >
   > <font color='green'>**Good**</font>:
   >
   > > Author | Commit | Message | Commit date
   > > ------ | ------ | ------- | -----------
   > > John, Doe | 1779a24xb92 | initial README work | 1 hours ago
   > > John, Doe | 886117771d8 | adding copy right reference file | 1 hour ago
   > > John, Doe | cxb9a2443a0 | adding changelog reference file | 2 hours ago
   > > John, Doe | 13x0360b4b7 | adding .gitconfig reference file | 2 hours ago
   > > John, Doe | 08b7f2fx462 | adding .gitignore reference file | 2 hours ago
   > > John, Doe | x8b7f2f6462 | Initial Commit | 4 hours ago
3. **Commit early, commit often, when still working on your branch**
   > commit local code often, this way your tech lead can review more often, not only when PR
   >
   > commit local code early, this will be an evidence that you started dev on current task
4. **Test Before You PR**
   > push your code through automated test which results evidence, before any PR
   >
   > if there are not automated tests, **push manual evidence to Jira Task**
5. **Always keep up to date before PR**
   > before PR, rebase you code from destination branch
   >
   > this will resolve conflicts before any review
   >
   > it will save time of your colleagues
6. **Use rebase strategy to fetch&merge new commits to your local branch**
   > before PR, rebase you code from destination branch
7. **Always clean-up before PR**
   > one mindset you should have is the least possible noise on main branches
   >
   > this means, that always have one, and only one commit pushed to PR on, let's say, master
   >
   > this will make an easy tagging or versioning for **Release Management** and easy to update changelog automatically
8. **Use [squash] for your local commits**
   > after you clean-up then you show remove the noise you can possible add to destination branch
   >
   > go to [Git CheatSheets] in **Clean-Up Operations** for detailed steps
9. **Don’t panic, merges conflicts are solvable, ask for help**
   > You will often have merge conflict, which are basically the same line of code modified by 2 authors
10. **Source Versioning(GIT) is not a backup**
   > git will not help you if you lose local branches, therefore you need additional backup mechanism 
11. **Agree on a git workflow principle and branching strategy**
   > This will improve you mindset on git operations add efficiency in the mid-term, once you get use to it.
   >
   > Also generate a basic hygiene of all working with repositories.
   >
   > Since we will all speak the same _language_ we wont loose time understanding repository workflow.
   >
   > It will also help building automation tools to PR process.

# <a name="gitworkflow"></a> Git WorkFlow
Below is an example on how branches should manifest on stable branching strategy:
   >    \-   | Derived from | Merged into | Life cycle
   > ------- | ------------ | ----------- | -----------
   > stable  | master tags  |      -      | infinite
   > master  |       -      |      -      | infinite
   > develop |       -      |   master    | infinite
   > feature |    develop   |   develop   | removed after PR
   > bugfix  |    develop   |   develop   | removed after PR
   > hotfix  |    stable    |   develop, master, stable | removed after PR
   > 
   > Stable and master branches will be evergreen.
   > 
   > Stable branch will NOT tempered after release. 
   > 
   > Example: 
   > > After ```stable/0.1.2``` release, this branch will never be modified again or delete.
   > > 
   > > The only exception is if there is a hotfix.
   >
   > Stable branches should be created during sprint end and include modifications during sprint scope.
   > 
   > Production environments will **allays** point to stable version.
   > 
   > Master should not be tempered by dev team, only by **Release Management**.
   > 
   > Master should have automated tests, to test the component integrity.
   > 
   > Support branches like: ```feature```, ```bufix```, ```hotfix``` should always PR into develop

# <a name="naming-conventions"></a> Naming Conventions
   >  Whenever you have a new task, and need to clone a new repo or checkout a branch, you should always keep a standard. 
   >
   >  Branch | Naming Convention
   > ------- | ------------
   > stable  | stable/1.1.1, stable/0.5.3
   > master  |       -      
   > develop |       -      
   > feature | feature/{jira task id}-{2-3 word summary}_{author initials}
   > bugfix  | bugfix/{jira task id}-{2-3 word summary}_{author initials}
   > hotfix  | hotfix/{jira task id}-{2-3 word summary}_{author initials}
   > 
   > Example:
   > > ```feature/JIRA-9876-new-customer-button_JD```
   > >
   > > ```feature/```  - branch prefix
   > >
   > > ```JIRA-9876``` - Jira Task ID
   > >
   > > ```new-customer-button``` - 2-3 word summary
   > >
   > > ```_JD``` - author initials, in this case John, Doe
   >  
   > For declarative deployments pushed to development or production environments it may differ.
   >  
   > In this situations a build pipeline is in place and _connects_ a branch with an actual environment
   > >  Environment | Naming Convention | Derived from
   > > ------------ | ----------------- | ------------
   > >  production  | deploy/prod-{1}-{2}-{3} | latest stable
   > >      qa      | deploy/qa-{1}-{2}-{3}   | latest stable
   > >    develop   | deploy/develop-{1}-{2}-{3} | latest stable, develop
   > >
   > > where {1},{2},{3} can be the GCP/AWS/AZ project id, customer abbreviation, component name or component version
   >
   > **This is where LCM tool can benefit the most, knowing what stable version is in prod and what you need to do to move it to newer version**

# <a name="branching-strategy"></a> Branching Strategy
   > ![Alt text](static/GitStableStrategy.svg)
   > 
   > Above you can see an example of a typical stable branch strategy.
   > 
   > ```master``` and ```stable``` are branches that only **Release Management** can tamper with.
   > 
   > Tags will be created by **Release Management** from master branch and pushed to new stable release.
   > 
   > Developers can only tamper with support branches: feature, bugfix, hotfix and PR to develop
   > 
   > ```hotfix``` branches will always checkout from stable release and PR back to it, master and develop.
   > 
   > ```bugfix``` branches will always checkout from develop and PR back to it.
   > 
   > ```feature``` branches will always checkout from develop and PR back to it.

# <a name="prprocess"></a> Pull Request Process
   > Pull requests let you tell others about changes you've pushed to a repository. 
   >
   > Once a pull request is sent, interested parties can review the set of changes, discuss potential modifications, and even push follow-up commits if necessary.
   >
   > There must be process in place before a PR can be created to avoid wasting reviewers time.
   > 
   > Example:
   > > 
   > > ```Rebase Destination Branch >> Fix Conflicts if any >> Clean-Up Code to Avoid Noise >> PR```
   >
   > Go to [Git CheatSheets] to **Clean-Up Operations** for more details.
   >
   > **What NOT to do when issuing or reviewing a PR:**
   > > <font color='red'>**Do not approve a PR without any understanding the code or it's purpose!**</font>
   > >
   > > <font color='red'>**Do not remove reviewers, once you add them, who flagged your PR as 'needs work', this is a good time to start learning!**</font>
   > >
   > > <font color='red'>**Do not remove reviewers, once you add them, just because they have suggestions!**</font>
   > >
   > > <font color='red'>**Do not issue a PR without a jira task, or without being part of Sprint Scope!**</font>
   > >
   > > <font color='red'>**Do not issue a PR without reading guidelines, naming convention, commit convention, etc.!**</font>
   > >
   > > <font color='red'>**Either PR issuer or reviewer, be reasonable, bring arguments and keep improving!**</font>

# <a name="semver"></a> Semantic Versioning
   > All projects should adheres to [Semantic Versioning] and understand it's value.
   > ```
   > 1.2.3 (b7f2f6) <- Build number, should correspond with a revision in source control, 1st 6 chars
   > ^ ^ ^
   > | | └─── Patch version
   > | └───── Minor version
   > └─────── Major version
   > 
   > Non-negative integers, and MUST NOT contain leading zeroes.
   > ```
   > > Patch version - bug fixes, hot fixes, spelling mistakes, formatting, doc updates
   > >
   > > Minor version - features, major bug fixes or hot fixes, component doc.
   > >
   > > Major version - UX changes, file format changes, libs changes, compatibility changes, API changes.
   >
   > Release Example:
   > > If you release the 1st non productive component you should have ```stable/0.1.0```
   > > 
   > > If your component have 3 new patches next stable is ```stable/0.1.1```
   > > 
   > > If your component have another 10 new patches next stable is ```stable/0.1.2```
   > > 
   > > If your component have 10 new features next stable is ```stable/0.2.0```
   > > 
   > > If your component have 6 new features and 2 new patches next stable is ```stable/0.3.0```
   > > 
   > > If your component is production ready next stable is ```stable/1.0.0```
   > > 
   > > If your component have 3 new features next stable is  ```stable/1.1.0```

# <a name="changelog"></a> Git ChangeLog
   > What is a changelog?
   > > A changelog is a file which contains a curated, chronologically ordered list of notable changes for each version of a project.
   > > 
   > > Changelog goes hand in hand with Semantic Versioning and Naming Convention.
   >
   > Why keep a changelog?
   > > To make it easier for users and contributors to see precisely what notable changes have been made between each release (or version) of the project.
   > >
   > > This will help production environments to track down every change added to prod.
   >
   > Who needs a changelog?
   > > PO, Release Management, consumers or developers who care about what's in the software. 
   > >
   > > When the software changes, people want to know why and how.
   > >
   > > This will help production environments to track down every change added to prod.
   > 
   > Example:
   > > it should always be named ```CHANGELOG.md``` for consistency.
   > > Go to [ChangeLog] for reference file.

# <a name="readings"></a> More Readings
   > [Semantic Versioning Readings](https://semver.org/spec/v2.0.0.html)
   >
   > [Changelog Readings](https://keepachangelog.com/en/1.0.0/)
   > 
   > [Atlassian Git Workflows](https://www.atlassian.com/git/tutorials/comparing-workflows/feature-branch-workflow)
   > 
   > [Atlassian Advanced Git](https://www.atlassian.com/git/tutorials/advanced-overview)
   > 
   > [Atlassian Tutorials](https://www.atlassian.com/git/tutorials)
   > 
   > [Gitignore Tool](http://www.gitignore.io)
>
# <a name="authors"></a> Authors
* **George, Dicu** - *Initial work*

[Git Ignore File]:.gitignore
[Git Config File]:.gitconfig
[ChangeLog]:CHANGELOG.md
[COPYRIGHT]:COPYRIGHT.md
[Git CheatSheets]:CHEATSHEET.md
[squash]:CHEATSHEET.md
[Semantic Versioning]:https://semver.org/spec/v2.0.0.html
