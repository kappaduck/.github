# Branches

## Strategy

When pulling a branch, you should rebase your changes on top of it. This will ensure that your changes are always on top of the latest changes.

### Pulling

```bash
git pull --rebase <remote>
```

> You can also set this as the default behavior when pulling:

```bash
git config --global branch.autosetuprebase always
```

### Pushing

Before pushing your branch, you should rebase your changes on top of the develop branch. This will ensure your branch is up to date with develop branch.

```bash
git rebase develop
```

## Develop

Develop branch is the default branch for the repository. It is the branch that is checked out when you clone/fork the repository.

* Branch is protected
* Can be deployed to testing (mostly use for beta versions)
* Pull request are required to merge into it

After a release or hotfix branch is merged into the main branch, the develop branch should be updated with the changes from the main branch. This can be done by rebasing the develop branch on top of the main branch.

```bash
git rebase main
```

## Main

Main branch is the branch that contains the latest stable version of the code.

* Branch is protected
* It deployed to production/nugets
* Only release and hotfix branches can be merged into it

When merging into main, it should be done using a merge. This will ensure that the commit history contains the develop branch commits and reduce the risk of conflicts.

The commit message should be in the following format:

`release: <project>-<version>`

## Feature

Feature branches are used to implement new features. They are branched off of the develop branch and merged back into it when the feature is complete.

Feature branches should be named using the following format:

`git switch -c feature/<issue>/<description>`

## Bugfix

Bugfix branches are used to fix bugs. They are branched off of the develop branch and merged back into it when the bug is fixed.

Bugfix branches should be named using the following format:

`git switch -c bugfix/<issue>/<description>`

## Release

Release branches are used to prepare a new release. They are branched off of the develop branch and merged into the `main` branch when the release is ready. Only bugfixes and documentation changes should be made on this branch.

Release branches should be named using the following format:

`git switch -c release/<version>`

## Hotfix

Hotfix branches are used to fix bugs in the main branch. They are branched off of the main branch and merged back into it when the bug is fixed.

Hotfix branches should be named using the following format:

`git switch -c hotfix/<issue>/<description>`
