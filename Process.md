Sourcetree process


Basic steps:
* To switch a branch :
  Using the left nav bar Branches-<branchname> doubleclick. A cirlce should appear next to the branch name.
* To Commit a change :
  1. Select the "Uncommited changes" in the history graph window to show the Staged/Unstaged file sections.
  2. Select the checkbox in the unstaged files section on lower left area (and doubleclicking it to add it to the staged area?)
  3. Click the Commit button on the upper menubar. Type in the necessary comment in the bottom comments section, but *always* unselect "Push Changes immediately to origin"
* Pulling a remote dev branch:
  * If you have local commits yet to be merged and want the comments on each of those to be retained in the dev branch, or you dont want a merge commit to be generated locally then choose the "Rebase instead of Merge" checkbox on the Pull dialog.
  * If a dev --> master merge has been commited and synced to the master and now you are pulling the dev branch to have it updated to match the master, then leave the "Rebase instead of merge" unchecked.
  * **Never** change the default selection of the dropdown of the branch to pull in the Pull dialog. If this is done, it will pull one remote branch into another completely messing up the repository.
* Pushing to the remote branch:
  1. Click the Push menubar button.
  2. **Never** change the default selection of the selected grid row which should be the current branch. **Never** check off the  "Select All" checkbox. You can do a "Push All tags" if you want.
  3. Clicking ok should complete the push.
* Rolling back the last N commits see [this](https://www.atlassian.com/git/tutorials/resetting-checking-out-and-reverting/commit-level-operations):
  * In case this was a local branch whose commits you want to roll back were never pushed to the remote repo, then use a *Reset* operation. This involves:
    1. While on the correctly selected current branch, In the upper History graph, Select the last commit you want to rollback to and rightclick it.
    2. Select the "Reset branchname to this commit"
    3. Would recommend that you use a mode of "Hard - discard all working copy changes". This will make you loose all the changes that were done in your working folders untill the selected commit. However this is the cleanest way to avoid any mismatches between the working folder, staging and index.
    4. Click ok. All the chagnes should be reversed and the working folder files should return back to the selected commit state.
  * In case you wanted to roll back changes that have already exist on the remote repo, the operation to be used is a *Revert*.
    1. A revert creates a new commit unlike a Reset operation which changes the commit history and is therefore very safe.
    2. In the History graph window select the commit you want to roll back to.
    3. Rightclick and "Reverse Commit" option, confirm to generate the new commit.
    4. Rightclick the newly generated commit and Amend the last commit to and put in your desired commit reversal comment.
    5. Push the revert commit to remote.
* Ammending the last commit comment that you have not pushed to remote:
  1. Assuming there is nothing staged or uncommited locally.
  2. Select the last commit that going to go out in the History graph section.
  3. On the LHS navbar select the File Status item under the Workspace.
  4. Place cursor in the empty text in the bottom line textbox for the "Commit Message". The box will expand to show the "Commit Options" dropdown to its right.
  5. Choose the "Ammend last Commit" to see the last commit comment. Edit it and then click commit.
  6.


* Resolving Conflicts on pull/merge:
  1. Each file which has a conflict will be listed in the conflicts window on the lower left hand section.
  2. Manually edit the section between the <<<< master branch and ending with the dev >>>> markers. Keep the needed code and remove the markers and the separator of ====
  3. In the left bottom section of Sourcetree, stage the resolved file.




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

To merge the dev branch into the master, ensure that no one is using the master branch in this duration. Also, close all open files in editors on the machine which is doing the merge. Then:
1. Switch to the master branch.
2. Do a pull on the master branch. We are going to assume that we have no local commits on master waiting to go out. Hence just do a pull without the rebase option.
3. Verify that the history shows local and origin on master to be the same. It should have been become a fast forward merge - see whether the last master local commit was extended linearly to add the new remote commits.
4. Switch to the dev branch.
5. Ensure that there are no pending commits locally and if so, do the process for pushing of local dev changes to the remote dev branch. Then do a pull.
6. Verify that the history shows local and origin are the same on the dev branch.
7. Switch to the master branch.
8. Click the merge menubar button.
9. The merge dialog asks you to select the commit to merge into the current tree. This means that it is implicitly looking for the branch to merge into the current branch. Always select the topmost commit in the dev branch (which should be showing as dev & origin/dev.)
10. *Never* choose a "Rebase instead of Merge" on the merge dialog.
11. Select the "Create a commit even if merge resolved by fast forward commit"
12. The merge should occur generating a local commit.
13. If there are conflicts, those will be listed in the lower left section. Resolve them and then move it to the staged area and then commit the whole thing.
14. Push the merge commit to remote.
15. Verify that the local master and origin/master history is showing the same commit on the HEAD. The master branch is now ready.
16. Switch to the dev branch.
17. Do a pull without rebase.
18. Verify that this also resulted in a fast forward merge. Then push this commit to remote.
19. Now the dev, origin/dev, master and origin/master should all have the same commit and be the HEAD.
