Sourcetree process


Basic steps:
* To switch a branch :
  Using the left nav bar Branches-<branchname> doubleclick. A cirlce should appear next to the branch name.
* To Commit a change :
  1. Select the checkbox in the unstaged files section on lower left area (and doubleclicking it to add it to the staged area?)
  2. Click the Commit button on the upper menubar. Type in the necessary comment in the bottom comments section, but *always* unselect "Push Changes immediately to origin"
* Pulling a remote dev branch:
  * If you have local commits yet to be merged and want the comments on each of those to be retained in the dev branch, or you dont want a merge commit to be generated locally then choose the "Rebase instead of Merge" checkbox on the Pull dialog.
  * If a dev --> master merge has been commited and synced to the master and now you are pulling the dev branch to have it updated to match the master, then leave the "Rebase instead of merge" unchecked.
  * **Never** change the default selection of the dropdown of the branch to pull in the Pull dialog. If this is done, it will pull one remote branch into another completely messing up the repository.
* Pushing to the remote branch:
  TBD
* Resolving Conflicts on pull:
  TBD



Working locally on the dev branch:

1. Switch to the dev branch.
2. Make necessary changes on the files.
3. Commit but not to origin.

When the local work is done and has to be pushed to the remote repo:
1. Make sure you are on the dev branch.
2. Ensure that there are no Unstaged or Staged files in the branch. If there are, commit them or undo them.
3. Do a Pull using the rules given for "Pulling a remote dev branch" above.
4. Resolve any issues - see Resolving conflicts process above.

When the local branch is ready to be pushed:
1. Click the Push menubar button to push to remote.
