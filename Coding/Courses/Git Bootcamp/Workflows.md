## Centralized Workflow
Everyone works on master branch

## Feature Branch Workflow
- `main` is the official project history
- multiple teammates can collaborate on a single _feature branch_ without polluting the `main` branch.
- Only once approved, *feature bracnhes* are merged into `main` branch.

## Fork & Clone
- *fork* a repo
- *clone* it onto your local machine, now `origin` is pointing to the *forked repo*.
- make changes locally then `push` to `origin`.
- To make sure your *local repo* is in sync with the *original repo*, add a new remote `upstream` that points to it.
- you cannot push directly to the *original repo*, you can only `pull` from it.
- Once work is *pushed* to `origin`, open a pull request on GitHub to merge changes into `upstream`.
- Reminder, always `pull` from `upstream`, before `push` to `origin`.

## pull requests
1. Do some work locally on a *feature branch*.
2. Push up feature branch to remote.
3. Open a *pull request* to request a merge of the feature branch into a *protected branch*.
4. Wait for it to be approved.

