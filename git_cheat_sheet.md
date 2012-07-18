Git Cheat sheet

tagging

    [git tag -a some_message] -add a tag
    [git tag -d some_message] -delete tag
    git push origin :refs/tags/some_message

reset (rollback to) a commit

    git reset --hard <tag/branch/commit id>


branches

    git branch -a --list all branches
    git checkout -b new-name-of-branch -- create a new branch as working copy.
    git branch -D <name-of-branch>  --delete branch local
    git push origin --delete <name-of-branch> --delete branch remote


Visually fix conflicts
git mergetool -t opendiff




WORKFLOW - single user:

for the first time

    git init . --starts up git in this directory
    git add . -- add any changes recently made
    git commit -am "message here" -- commit changes to branch
    git remote add origin git@github.com:<username>/app_name.git
    git push origin master-- upload files to remote server
    git push heroku-cedar master - push app to Heroku


rinse and repeat
    
    git add . -- add any changes recently made
    git commit -am "message here" -- commit changes to branch
    git push --tags -- upload files to remote server
    git checkout -b new-name-of-branch -- create a new branch as working copy.


work on files locally
    
    git status ---shows what branch your on (you'll need this in a moment)
    git add . -- add any changes made
    git commit -am "message here" -- commit changes to branch


merge files back to remote server
   
    git checkout master
    git merge name-of-branch-just-worked-on
    git push --tags --upload files to remote server


Now you want to work on a new feature so:
    
    git checkout master
    git checkout -b name-a-new-branch-here


WORKFLOW - multi user:

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



General commands:

.gitignore (Edit this file to add files you want git to ignore.)

.gitconfig (Edit this file to add custom aliases.)

git clone [url] (copies a remote git repo to local)

git pull [server][branch] (updates your local repo with server repo.)

git remote add


More General git commands...

What branch am I on:
    
    git branch -a


create new local branch
    
    git checkout -b name-a-new-branch-here


create / push new local branch to remote
    
    git push origin <new branch name>

Switch branches (with uncommitted changes):
[step1]
git stash
git checkout [branch name]
[step2]
git stash apply


How to make a git alias:
(edit ~/.gitconfig  add this -[alias]- to the file)

At your command prompt type
(for textmate)
    
    $prompt mate ~/.gitconfig

(for vim)

    $prompt vim ~/.gitconfig

Place this inside...

    [alias]
    	st		= status -s -b
    	di		= diff
    	co		= checkout
    	com		= commit -am
    	br		= branch -a
    	chs 	= !git checkout $1 && git status
    	swi 	= !git stash && git checkout

    	pr 		= pull --rebase
    	prom 	= pull --rebase origin master	
    	l       		= "!source ~/.githelpers && pretty_git_log"
      	me   		= "!source ~/.githelpers && pretty_git_log --author=thefonso"
    	lp      	= log --pretty="format:'%h %ad | %an - %s%d'" --date=short
    	lgs     	= log --stat
    	ls      	= ls-files
    	fixup 	= commit --amend -C HEAD				
    	timeline = log --graph --branches --pretty=oneline --decorate
    	h = log --pretty=format:'%h - %an, %ar : %s'			
    	history = log --pretty=format:'%h - %an, %ar : %s'