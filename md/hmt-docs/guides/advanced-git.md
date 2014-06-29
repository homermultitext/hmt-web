# Using `github` to contribute to the HMT project

## Background ##


See a guide to [using git to work on HMT editions](basic-git.html)


## Forking, Pull-Requests, Merging ##

 `github` help pages:

-  "Fork a repo": <https://help.github.com/articles/fork-a-repo>.
- "Using pull requests":  <https://help.github.com/articles/using-pull-requests>


## One-time set up
1. From the `github` web interface, fork the repository.
1. Clone the fork to your machine (e.g., `git clone FORKEDREPOSITORYNAME` from a terminal on your machine.)
1. `git remote add upstream URL-TO-ORIGINAL-REPO` Lets your fork know where the original repo is.


## Normal work cycle ##


1. `git fetch upstream` and `git merge upstream/master` Grabs any changes from the original repository and merges them into your fork.
1. Work normally in your local clone of the forked repository.
1. When you have completed some work, go through the normal `git` cycle:   `git add FILE`, `git commit`
1. `git push origin master` Adds  your changes to your own forked repository.

To have work you have pushed to your forked repository integrated back into the original HMT repository you forked,

1. From the `github` web interface, submit a Pull Request.
