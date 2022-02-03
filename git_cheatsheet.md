# Git cheat sheet

## Common commands

- status
  - `git status`: show the working tree status, unstaged and staged files
- add
  - `git add foo.py`: add `foo.py` to the staging area
  - `git add foo.py bar.py`: add `foo.py` AND `bar.py` to the staging area
  - `git add -u`: Adds all tracked files to the staging area.
- rm
  - `git rm oops.txt`: remove `oops.txt`
- commit
  - `git commit -m "commit message"`:  See [here](https://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html) for commit message guidelines. Commit messages should be short, should be written as commands, and should not have ending punctuation.

    Example of a good commit message: `Add readme`

    Example of an bad commit message: `Adds readme.`
  - `git commit`: Opens your default text editor to write a commit message.
  - `git commit --amend`: changing the last commit message. Read more [here][fix-commit]
- log
  - `git log`: show commit logs
  - `git log --oneline | head`: To quickly see the latest ten commits on a branch.
- branch management
  - `git checkout new-branch-name`: create a branch with name `new-branch-name`
  - `git checkout new-branch-name`: switch to new branch `new-branch-name`
  - `git checkout -b new-branch-name`: create branch `new-branch-name` and switch to/check out that new branch
  - `git checkout main`: switch to your `main` branch
  - `git checkout old-branch-name`: switch to an existing branch `old-branch-name`
  - `git branch -v`: list all branches. "*" indicates current active branch
  - `git branch -d branch-name`: delete brach with name `branch-name`
- clone
  - `git clone link_to_repo`: clone remote repository in local
- remote
  - `git remote -v`: display your remote repositories
  - `git remote add upstream link_to_another_repo`: add another remote with name upstream 
- fetch
  - `git fetch origin`: fetch origin repository
  - `git fetch upstream`: fetch upstream repository
- pull
  - `git pull --rebase remote-name main`: rebase your changes on top of `main`.
  - `git pull` (with no options): Will either create a merge commit
    (which you don't want) or do the same thing as `git pull --rebase`,
    depending on [whether you've configured Git properly][git-config-clone]
- push
  - `git push origin branch-name`: push you commits to the origin repository _only if_ there are no conflicts.
    Use this when collaborating with others to prevent overwriting their work.
  - `git push origin +branch-name`: force push your commits to your origin repository. Don't do it unless you know what you are doing. 
- config
  - `git config --global core.editor nano`: set core editor to `nano` (you can set this to `vim` or others)
  - `git config --global core.symlinks true`: allow symbolic links
- diff
  - `git diff`: display the changes you have made to all files
  - `git diff --cached`: display the changes you have made to staged files
  - `git diff HEAD~2..`: display the 2 most recent changes you have made to files
- rebase
  - `git rebase -i HEAD~3`: interactive rebasing current branch with first three items on HEAD
  - `git rebase -i main`: interactive rebasing current branch with `main` branch
  - `git rebase upstream/main`: rebasing current branch with `main` branch from upstream repository
- grep
  - `git grep update_unread_counts static/js`: Search our JS for references to update_unread_counts.
- reflog
  - `git reflog | head -10`: manage reference logs for the past 10 commits
- reset
  - `git reset HEAD~2`: reset two most recent commits
- revert
  - `git revert`: reverse commit changes by new commit
  - `git revert HEAD...HEAD~2`: everse commit changes by new commit 2 commits behind
- show
  - `git show HEAD`: display most recent commit
  - `git show HEAD~~~`: display third most recent commit
  - `git show main`: display most recent commit on `main`

See also [fixing commits][fix-commit]

[fix-commit]: https://github.com/zulip/zulip/blob/main/docs/git/fixing-commits.md
[git-config-clone]: https://zulip.readthedocs.io/en/latest/git/cloning.html#step-1b-clone-to-your-machine
[git-overview]: https://github.com/zulip/zulip/blob/main/docs/git/overview.md


Inspired and modified from: [Zulip git doc](https://github.com/zulip/zulip/blob/main/docs/git/cheat-sheet.md)