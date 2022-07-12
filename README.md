# crispy-octo-tribble

### Part 1
---
Every 3 weeks, as part of our release process, we create a release branch in our git repositories
from the commit we would like to release. Branch names follow the “release/[version]” naming
convention, where the version is a semantic version, e.g. 1.66.0. For each release branch, we
increment the version. Creating the branches manually has the potential for error, and we
would also like to increase the frequency at which we release, so we would like to automate this
process.

Please implement an automatic way to create these release branches in our git repositories.
Your solution should also automatically increment the version from the previous release, and
should run on a regular schedule.


### Solution
---
To generate an automatic procedure with the specified requirements, I created a couple of GitHub
Actions that work over the repository.

**[create_release_branch](https://github.com/gctrevino/crispy-octo-tribble/actions/workflows/create_release_branch.yml)** that generates a release branch on schedule, but it can also be triggered manually

**[publish_release](https://github.com/gctrevino/crispy-octo-tribble/actions/workflows/publish_release.yml)** that after the release branch gets generated, create a release for the new release branch

### To run it
---
The quickest way to make this run is by manually triggering the action [create_release_branch](https://github.com/gctrevino/crispy-octo-tribble/actions/workflows/create_release_branch.yml)

Alternatively, the schedule can be modified to make it run automatically as needed.

```
  schedule:
    - cron: '30 5 11 * *'
    - cron: '30 5 21 * *'
```

### ToDo
---
The calculation of the version is currently only considering the lower number (PATCH), a logic where according to the comments in the changes implemented should be added to calculate when to add to the MAJOR and MINOR parts of the version.

Failsafe locks are missing from the actions, there is only a try-catch implemente that was left because of a test, but locks should be set in place to avoid unsync among the releases and branches.

### Alternatives
---
There are other premade solutions that automagically gather the release notes based on the comments such as [semantic-release](https://semantic-release.gitbook.io/semantic-release/) but that would require a commitment from the developers to respect such standards or implement a prehook solution such as (husky)[https://typicode.github.io/husky] to enforce them.



