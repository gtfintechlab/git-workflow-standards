# Git cheat sheet

## Common commands

- status
  - `git status`: show the working tree status, unstaged and staged files
- add
  - `git add foo.py`: add `foo.py` to the staging area
  - `git add foo.py bar.py`: add `foo.py` AND `bar.py` to the staging area
  - `git add -u` or `git add .`: Adds all tracked files to the staging area.
    - Note: If you want to use `git add .`, make sure that you are at the root directory of your project, otherwise it will only add the files that are in the current working directory.
- rm
  - `git rm oops.txt`: remove `oops.txt`
- commit
  - `git commit -m "commit message"`:  See [here](https://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html) for commit message guidelines. Commit messages should be short, should be written as commands, and should not have ending punctuation.

    Example of a good commit message: `Add readme`

    Example of an bad commit message: `Adds readme.`
  - `git commit`: Opens your default text editor to write a commit message.
  - `git commit --amend`: Commit the current staged files into previous commit and also changing the last commit message. Read more [here][fix-commit]
  - `git commit --amend --no-edit`: Commit the current staged files into previous commit without changing the commit message.
- log
  - `git log`: show commit logs
  - `git log --author="Michael"`: show commit logs authored by `Michael`.
  - `git log --oneline | head`: To quickly see the latest ten commits on a branch.
  - `git log --oneline --graph`: One line log with graphical representation if there are merge commits.
- branch management
  - `git checkout branch-name`: switch to branch `branch-name`
  - `git checkout -b new-branch-name`: create branch `new-branch-name` and switch to/check out that new branch
  - `git checkout main`: switch to your `main` branch
  - `git checkout old-branch-name`: switch to an existing branch `old-branch-name`
  - `git branch -v`: list all branches. "*" indicates current active branch
  - `git branch -d branch-name`: delete brach with name `branch-name`.
  - `git branch -D branch-name`: Hard delete brach with name `branch-name`
  - `git branch -m new-branch-name`: Change the current branch name to `new-branch-name`
- clone
  - `git clone link_to_repo`: clone remote repository in local
- remote
  - `git remote -v`: display your remote repositories
  - `git remote add upstream link_to_another_repo`: add another remote with name upstream 
- fetch
  - `git fetch origin`: fetch origin repository
  - `git fetch upstream`: fetch upstream repository
  - `git fetch origin branch-name`: fetch the branch `branch-name` origin repository
- pull
  - `git pull --rebase remote-name main`: rebase your changes on top of `main`.
  - `git pull` (with no options): Will either create a merge commit
    (which you don't want) or do the same thing as `git pull --rebase`,
    depending on [whether you've configured Git properly][git-config-clone]
- push
  - `git push origin branch-name`: push you commits to the origin repository _only if_ there are no conflicts.
    Use this when collaborating with others to prevent overwriting their work.
  - `git push origin branch-name -f`: force push your commits to your origin repository. Don't do it unless you know what you are doing. Do it only after you have rebased.
- config
  - `git config --global core.editor nano`: set core editor to `nano` (you can set this to `vim` or others)
  - `git config --global core.symlinks true`: allow symbolic links
- diff
  - `git diff`: display the changes you have made to all files
  - `git diff --cached`: display the changes you have made to staged files
  - `git diff HEAD~2..`: display the 2 most recent changes you have made to files
  - `git diff branch_one branch_two`: display the changes between `branch_one` and `branch_two`.
  - `git diff branch_name`: display the changes between `current_branch` and `branch_name`.
- rebase
  - `git rebase -i HEAD~3`: interactive rebasing current branch with first three items on HEAD
  - `git rebase -i main`: interactive rebasing current branch with `main` branch
  - `git rebase upstream/main`: rebasing current branch with `main` branch from upstream repository. Do it when you have conflicts with main branch in your pull request.
- grep
  - `git grep update_unread_counts static/js`: Search our JS for references to update_unread_counts.
- reflog
  - `git reflog | head -10`: manage reference logs for the past 10 commits
- reset
  - `git reset HEAD~2`: reset two most recent commits, and brings their changes in unstaged mode.
- revert
  - `git revert`: reverse commit changes by new commit
  - `git revert HEAD...HEAD~2`: reverse commit changes by new commit 2 commits behind
  - `git revert commit_hash`: reverse the commit with commit hash = `commit_hash`
- show
  - `git show HEAD`: display most recent commit
  - `git show HEAD~~~`: display third most recent commit
  - `git show main`: display most recent commit on `main`
  - `git show commit_hash`: display the commit with commit hash = `commit_hash`
- cherry-pick
  - `git cherry-pick commit_hash_1 commit_hash_2`: Add commits with given commit hashes in current branch in given order.
- stash
  - `git stash`: Undo all the staged and unstaged changes and push them into stack so that you can use it later on. (Use it when you need to work in different branch and circle back to current branch after that)
  - `git stash push -m "my_stash"`: Same as above, just give your stash a name to track.
  - `git stash apply`: Redo the last stashed work. (Pop from the stack)
  - `git stash list`: List all the stashed work (From stack).
  - `git stash apply stash@{n}`: Redo nth stashed work from top of stack.

See also [fixing commits][fix-commit]

[fix-commit]: https://github.com/zulip/zulip/blob/main/docs/git/fixing-commits.md
[git-config-clone]: https://zulip.readthedocs.io/en/latest/git/cloning.html#step-1b-clone-to-your-machine
[git-overview]: https://github.com/zulip/zulip/blob/main/docs/git/overview.md


Inspired and modified from: [Zulip git doc](https://github.com/zulip/zulip/blob/main/docs/git/cheat-sheet.md)