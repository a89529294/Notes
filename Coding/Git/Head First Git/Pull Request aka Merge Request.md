# Anatomy of a Pull Requests
When you file a pull request, all you’re doing is _requesting_ that another developer _pulls_ a branch from your repository into their repository.

That means you have to specify fout things:
1. source repo
2. source branch
3. destination repo
4. destination branch
*destination* means repo/branch to integrate into
*source* usually means repo/branch you wish to integrate into the *destination*

## General Steps
1. A developer creates the feature in a dedicated branch in their local repo.
2. The developer pushes the branch to a public Bitbucket repository.
3. The developer files a pull request via Bitbucket.
4. The rest of the team reviews the code, discusses it, and alters it.
5. The project maintainer merges the feature into the official repository and closes the pull request.