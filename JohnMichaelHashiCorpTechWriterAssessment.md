### The differences between the push, pull, and fetch commands

There are two important differences between each of these three commands: the number of operations (actions) that occur when you run a command, and the direction in which data flows when you run a command.

- `git push` - uploads (exports) commits from your local repo to a remote repo.
- `git fetch` - downloads (imports) changes from a remote repo to your local repo, but does not merge these changes into your local repo.
- `git pull` - downloads changes from a remote repo and merges them into your local repo.

When you run the `git push` command, Git checks your local repo to see if there is a tracking branch connected to the branch you are currently working in. If there is a tracking branch, then your commits are taken from your local branch and are pushed to the remote repo. Specficially, the commits are pushed to the remote-tracking branch in the remote repo that corresponds to the tracking branch in your local repo. This is how code is shared with a remote repository. You can think of this operation as "making the remote branch resemble your local branch".

The `git push` operation will fail if the remote branch has diverged from your local branch. Rephrased, the operation will fail unless all of the commits in the remote branch are already in your local branch. When `git push` fails, your local branch needs to be synchronized with the remote branch. You can accomplish this synchronization by using just the `git pull` command, or by using `git fetch` followed by `git merge`.

The `git fetch` command has Git check your local repo to see if there is a tracking branch connected to the branch you are currently working in. If there is a tracking branch, then Git checks the remote-tracking branch (which is in the remote repo) for any changes, and then pulls any changes into your tracking branch. The changes are not merged into your local branch. You have the opportunity to review the changes in the tracking branch so that you can decide if you want to merge them into your local branch. Use the `git merge origin/master` (for the "master" branch) command to merge those changes into your branch.


The `git pull` command runs a `git fetch` operation followed immediately by `git merge`. Using `git pull` does not provide you with an opportunity to review changes before they are made to your local branch. However, `git pull` does save time when you already know what changes you are allowing into your local repo.

