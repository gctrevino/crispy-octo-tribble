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

**create_release_branch** that generates a release branch on schedule, but it can also be triggered manually
**publish_release** that after the release branch gets generated, create a release for the new release branch


https://semantic-release.gitbook.io/semantic-release/

