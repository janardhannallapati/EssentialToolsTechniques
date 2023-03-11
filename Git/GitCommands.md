# Rollback

## How to rollback a rebase

`$ git reflog`

b710729 HEAD@{0}: rebase: some commit

5ad7c1c HEAD@{1}: rebase: another commit

deafcbf HEAD@{2}: checkout: moving from master to my-branch

`$ git reset HEAD@{2} --hard`

Now you should be back to before the rebase started.

To find the right place to reset to, you just pick the entry closest 

to top that doesn't start with "rebase".

Alternative approach

If the rebase is the only thing you have done on the branch, 

i.e. you have no unpushed commits/changes - 

then you could just delete the local branch with 

`git branch -D `

and then check it out again:

`$ git checkout my-branch`

`$ git rebase master`

// not happy with result`

`$ git checkout master`

`$ git branch -D my-branch`

`$ git checkout my-branch`

Or for the same effect, you could reset --hard to the origin branch:

`$ git reset --hard origin/my-branch`

If you did do this while you had other unpushed commits, 

then you will have lost them. In that case just use

the reflog approach above to jump back to the reflog entry 

where you made the commit(s).

# Move files around
## To get a file from another branch into your current branch
`git checkout branchname path_to_file_name`
