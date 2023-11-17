# git-commands

## Install

Add this folder to your path, so `git` can pick up the scripts.

## Commands

### Start

**Pulls main and creates a new feature branch named `feature`.**

`git start [feature]`

### Sync

**Pulls main and rebases working branch.**

`git sync [-i]`

This is useful to avoid your changes being interleaved with other commits.
For example, say you were coding in your branch and made the changes `A, B, C`.
If you merge with main the commit history may now be `W, A, X, Y, B, Z, C`.
Leaving the history like this can make it harder to rollback a logical set of
changes in one go. Using rebase, you will replay your commits on the end of
main, resulting in `W, X, Y, Z, A, B, C`.

Often it makes sense to make a lot of changes locally, that you wouldn't
necessarily want to push together, in cases like this you can use
`git sync -i` to interactively rebase your changes and squash some commits.
This can result in a commit history showing `W, X, Y, Z, D`.

Much cleaner, right? But do be careful that you understand what is going on as
rebase can both squash and remove commits.

### Squash

`git squash`

Squashes all commits on the current branch since its divergence from the main branch into a single commit:

### Shove

`git shove`

Pushes the current local Git branch to the 'origin' remote, after ensuring there are no uncommitted changes and the branch isn't the main branch. It also checks if the branch is new or needs updating on the remote.

## License

This is a fork from: https://github.com/dpup/git-workflow. It keeps `git-start` and `git-sync` but converts them to bash for less dependencies. It adds `git-squash` and `git-shove`.
