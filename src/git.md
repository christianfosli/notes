# Git quick-ref :tanabata_tree:

Open help-page: `git help command`

* Everyday work

  * Check what's up       `git status`

  * See what happened     `git log [--graph --date=human --stat]`)

    * one-line commits: `git log [--graph] --oneline`

    * show the patch: `git log [--graph] -p`

  * Add files to stage    `git add filename`

    * Stage part of file  `git add -p filename`

  * Unstage file          `git restore --staged <filename>`

  * Check diff            `git diff branch1 branch2`  or `file1 file2` etc

    * Check message and diff of commit: `git show <commit-hash>`

    * Check diff for a merge commit:

      * Given this commit:
      ```patch
      commit ccc333
      Merge: aaa111 bbb222 
      ```

      ```console
      git diff aaa111...bbb222
      ```

    * Exclude specific file from diff: `git diff -- . ':!package-lock.json'` or `git show HEAD -- . ':!Cargo.lock'`

  * Commit stage to current branch `git commit`

    * Commit all tracked files with changes: `git commit -a`

    * Use interactive patch selection to decide what to commit: `git commit -p`

    * Show diff below the commit message: `git commit -v`

  * Restore file to HEAD  `git restore <filename>`

  * Restore file to branch `git restore -s <branchname> <filename>`

* Misc

  * Does origin/master have new commits? (commits not reachable from HEAD)

    `git fetch origin && git log ..origin/master`

  * Ignore future local changes to a tracked file (useful for config files...)
    `git update-index --skip-worktree <filename>`

    * Undo with `git update-index --no-skip-worktree <filename>`

  * Apply patch (3-way merge)

    `git show <sha1> | git apply -3`

* Branches

  * Show branches         `git branch` or `git branch -vv` or `git branch -r`
  
  * Create branch         `git branch <branch-name>`

  * Switch to branch      `git switch <branch>`

  * Do both 2 above       `git switch -c <branch name>`

  * Merge/rebase branch   *first checkout the to-branch* then
                          `git merge <from-branch>` or `git rebase <from-branch>`

  * Delete branch         `git branch -d <branch>`
                          force delete with `git branch -D <branch>`

  * Delete every branch except master `git branch | grep -v "master" | xargs git branch -D`

  * Reset branch to earlier commit / branch / tag `git reset --hard <commit>`

  * Clean up latest n commits (opens interactive rebase editor letting you squash, pick, fixup, reorder)

     `git rebase -i HEAD~n`

  * Rebase _and_ update intermediate "feature branches" `git rebase --update-refs`

* Remotes

  * Fetch latest changes  `git fetch <remote>`

    * And remove remote remote tracking branches which have been deleted
    `git fetch -p <remote>` (shows [gone] on `git branch -v`)

  * Show remote info      `git remote -v` or more info with `git remote show <remote>`

  * Fetch and merge       `git pull`

  * Push to remote        `git push <remote> <branch> [--force-with-lease]`

  * Push and add upstream (tracking) reference `git push -u <remote> <branch>`

  * Delete remote branch  `git push <remote> -d <branch>`

  * Update submodules     `git submodule update` or `git submodule update --remote`

* Finding commits

  * Search by author: `git log --author <name>`

  * Search by commit message: `git log --grep <regexp>`

  * Search by patch text (i.e. diff content): `git log -G <regexp>`
