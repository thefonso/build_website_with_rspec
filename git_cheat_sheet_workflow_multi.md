WORKFLOW - MULTI user:

For the first time
    
    git clone git@github.com:<username>/app_name.git


Now you want to work on a feature so:
    
    git checkout -b [name of branch]


Rebase against the upstream frequently to prevent your branch from diverging significantly:
    
    git fetch origin master
    git rebase origin/master


We want the rebase to affect only the commits we’ve made to this branch, not the commits that exist on the upstream. To ensure that we only deal with the “local” commits, use:
    
    git rebase -i origin/master


Git will display an editor window with a list of the commits to be modified, something like:

    pick 3dcd585 Adding Comment model, migrations, spec
    pick 9f5c362 Adding Comment controller, helper, spec
    pick dcd4813 Adding Comment relationship with Post
    pick 977a754 Comment belongs to a User
    pick 9ea48e3 Comment form on Post show page


Now we tell git what we to do. Change these lines to:

    pick 3dcd585 Adding Comment model, migrations, spec
    squash 9f5c362 Adding Comment controller, helper, spec
    squash dcd4813 Adding Comment relationship with Post
    squash 977a754 Comment belongs to a User
    squash 9ea48e3 Comment form on Post show page


Save and close the file. This will squash these commits together into one commit and present us with a new editor window where we can give the new commit a message, something like:

    [#3275] User Can Add A Comment To a Post

    * Adding Comment model, migrations, spec
    * Adding Comment controller, helper, spec
    * Adding Comment relationship with Post
    * Comment belongs to a User
    * Comment form on Post show page


Note:This also follows Tim Pope’s git commit message best
practices. Now, save and close your editor.

This commit is now ready to be merged back into master. First rebase against any recent changes in the upstream. Then merge your changes back into master:

    git checkout master
    git merge 3275-add-commenting


And finally, push your changes to the upstream:
    
    git push origin master


