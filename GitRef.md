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

`git log --oneline` more concise

`git checkout [specificCommitHash]` -- checks out specific hash

`git checkout [branchName]^` -- moves up one commit (parent)
`git checkout [branchName]^^` -- moves up two commits (grandParent)

`git checkout HEAD^` -- moves up one commit from the current reference.  `HEAD` is relative. Calling this 3 times will move upwards 3 times

`git checkout [branchName]~n` -- moves up `n` number of commits from `branchName`

`git checkout HEAD~n` -- moves up `n` number of commits from current reference

You can directly reassign a branch to a commit with the `-f` option, something like

`git branch -f master HEAD~3`

###Force Push

If you've rebased your feature branch and want to push it to master, you'd force push

`git push origin <#featureBranchName#> -f`

If checked out, this might work. 

`git push -f`

###Reversing Changes

`git revert`

`git reset` -- resets as if commit had never been made in the first place.

`git reset HEAD~1` -- resets last commit at current head

Resetting is great for local branches on your own machine, its method of rewriting history doesn't work for remote branches that others are using.

In order to reverse changes and share those reversed changes with others, use `git revert`

`git reset --hard <#commitSHAH#>` Reset to that commit

##Rename branch:

`git branch -m <oldname> <newname>`

If you want to rename the current branch, you can simply do:

`git branch -m <newname>`

##Stash

`git stash`
- stash current working directory

`git stash apply`
- apply the last created stash

`git stash save "my_stash"`
- save stash with name

`git stash apply stash^{/my_sta}`
- apply stash with name.  subscribes to regex, so my_sta would likely find my_stash.  In general, I type the entire name.

`git stash list`
- List all stashes

`git stash pop stash@{n}`
- apply stash at index n and remove from stash stack

`git stash apply stash@{n}`
- apply stash at index n and keep in stash stack


###Adding a GitIgnore

```
# Xcode
#
build/
*.pbxuser
!default.pbxuser
*.mode1v3
!default.mode1v3
*.mode2v3
!default.mode2v3
*.perspectivev3
!default.perspectivev3
xcuserdata
*.xccheckout
*.moved-aside
DerivedData
*.hmap
*.ipa
*.xcuserstate

# CocoaPods
#
# We recommend against adding the Pods directory to your .gitignore. However
# you should judge for yourself, the pros and cons are mentioned at:
# http://guides.cocoapods.org/using/using-cocoapods.html#should-i-ignore-the-pods-directory-in-source-control
#
# Pods/
```

From <a href="https://github.com/github/gitignore/blob/master/Objective-C.gitignore">here!</a>

#Tags

Ref: <a href="http://git-scm.com/book/en/Git-Basics-Tagging">http://git-scm.com/book/en/Git-Basics-Tagging</a>

Add a tag

`git tag -a <#tagName#> -m "<#description#>"`

Add a tag to an older commit

`git tag -a <#tagName#> -m "<#description#>" <#commitSHAHRef`

  example: `git tag -a v1.2 -m 'version 1.2' 9fceb02`

Push a tag

`git push origin <#tagName#>`

Push all tags

`git push origin --tags`

List Tags

`git tag`

See tagged commit

`git show <#tagName#>`

#Ignore Local Changes To Specific File

There are some cases where you want to ignore changes to a specific file.  For example, I have a project that has safeguards preventing non authorized users from getting to a certain part of the application.  I need to access this part of the application, so I remove these safeguards.  I never want to push this file up, and I don't want to add it to the .gitignore, so I can use --assume-unchanged

`git update-index --assume-unchanged Path/To/File.m`

To list all files currently in assume-unchanged mode:

`git ls-files -v | grep -e "^[hsmrck]"`

To remove all files from assume-unchanged mode:

`git --no-assume-unchanged`

#Submodules

-- DON'T USE SUBMODULES IF AT ALL POSSIBLE!!!!!!!!

Update and Init

`git submodule update --init --recursive`
