### The differences between the push, pull, and fetch commands

There are two important differences between each of these three commands: the number of operations (actions) that occur when you run a command, and the direction in which data flows when you run a command.

- `git push` - uploads (exports) commits from your local repo to a remote repo.
- `git fetch` - downloads (imports) changes from a remote repo to your local repo, but does not merge these changes into your local repo.
- `git pull` - downloads changes from a remote repo and merges them into your local repo.

When you run the `git push` command, Git checks your local repo to see if there is a tracking branch connected to the branch you are currently working in. If there is a tracking branch, then your commits are taken from your local branch and are pushed to the remote repo. Specficially, the commits are pushed to the remote-tracking branch in the remote repo that corresponds to the tracking branch in your local repo. This is how code is shared with a remote repository. You can think of this operation as "making the remote branch resemble your local branch".

The `git push` operation will fail if the remote branch has diverged from your local branch. Rephrased, the operation will fail unless all of the commits in the remote branch are already in your local branch. When `git push` fails, your local branch needs to be synchronized with the remote branch. You can accomplish this synchronization by using just the `git pull` command, or by using `git fetch` followed by `git merge`.

`git fetch` again takes our current branch, and checks to see if there is a tracking branch. If so, it looks for changes in the remote branch, and pulls them into the tracking branch. It does not change your local branch. To do that, you'll need to do `git merge origin/master` (for the "master" branch) to merge those changes into your branch - probably also called "master".`git pull` simply does a `git fetch` followed immediately by `git merge`. This is often what we desire to do, but some people prefer to use git fetch followed by git merge to make sure they understand the changes they are merging into their branch before the merge happens.
