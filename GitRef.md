Good Practice: http://pcottle.github.io/learnGitBranching/

`git commit` - make a commit on the currently checked out branch

###New Branch

`git branch [branchName]` - creates a new branch at current commit pointer
`git checkout [branchName]` - checks out a new branch

or

`git checkout -b [branchName]` - creates and checks out a new branch at current commit pointer

###Merging

`git merge [branchName]` - merges [branchName] into the currently checked out branch

essentially says "I want to include all the work from this parent over here and this one over here, <i>and</i> the set of all their parents."

###Rebasing

Essentially takes a set of commits, "copies" them, and plops them down somewhere else. 

`git checkout [branchName]` 
`git rebase [differentBranchName]` -- takes current branch and moves it to the top of `differentBranchName`

Use `git rebase -i [differentBranchName]` -- walks through each commit of current branch to deal with conflicts step by step

`git checkout [differentBranchName]` -- switch to the branch we just added on top of
`git rebase [branchName]` -- moves`differentBranchName` pointer to the top of `branchName`. Because `differentBranchName` is an ancestor of `branchName` git simply moves the `differentBranchName` reference forward. Both should be pointing to the same place now.

###Checking out a specific commit

`git log` displays hashes

`git checkout [specificCommitHash]` -- checks out specific hash

`git checkout [branchName]^` -- moves up one commit (parent)
`git checkout [branchName]^^` -- moves up two commits (grandParent)

`git checkout HEAD^` -- moves up one commit from the current reference.  `HEAD` is relative. Calling this 3 times will move upwards 3 times

`git checkout [branchName]~n` -- moves up `n` number of commits from `branchName`

`git checkout HEAD~n` -- moves up `n` number of commits from current reference

You can directly reassign a branch to a commit with the `-f` option, something like

`git branch -f master HEAD~3`

###Reversing Changes

`git revert`

`git reset` -- resets as if commit had never been made in the first place.

`git reset HEAD~1` -- resets last commit at current head

Resetting is great for local branches on your own machine, its method of rewriting history doesn't work for remote branches that others are using.

In order to reverse changes and share those reversed changes with others, use `git revert`



