# gha-sync-fork

A GitHub action to sync a forked repo's branch with an upstream repo's branch

## Overview

The fork's changes are rebased on top of any missing commits from the upstream
repository. If there are merge conflicts, this action will fail until the conflicts
are manually resolved. If there are no changes between the fork and upstream, no work
is done. By default, the fork's entire commit history is fetched because this action
doesn't know how many new commits the fork has received.

[![.github/workflows/test.yml](https://github.com/thebrowsercompany/gha-sync-fork/actions/workflows/test.yml/badge.svg)](https://github.com/thebrowsercompany/gha-sync-fork/actions/workflows/test.yml)


## Usage

An example workflow that runs this action:

```yml
- name: Sync my project
  uses: thebrowsercompany/gha-sync-fork
  with:
    fork_repo: myuser/project
    fork_branch: main
    upstream_repo: otheruser/project
    upstream_branch: main
```

### Inputs

```yml
fork_repo:
  description: The repository to update.
  required: false

fork_branch:
  description: The branch to update.
  required: true

upstream_repo:
  description: The repository to pull changes from.
  required: true

upstream_branch:
  description: The branch to pull changes from.
  required: true

upstream_host:
  description: The upstream repository URL host, if not github.com.
  required: false
  default: 'github.com'

dry_run:
  description: If true, changes are not pushed to the fork.
  required: false
  default: false
```
