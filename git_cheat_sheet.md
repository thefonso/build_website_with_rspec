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

general commands
.gitignore 
Edit this file to add files you want git to ignore.
.gitconfig
Edit this file to add custom aliases.

git clone [url]
copies a remote git repo to local

git pull [server][branch]
updates your local repo with server repo.

git remote add

gpush lives in .bash_profile

useful tool: gitolite (google is your friend)


WORKFLOW - single user:

for the first time

    git init . --starts up git in this directory
    git add . -- add any changes recently made
    git commit -am "message here" -- commit changes to branch
    git remote add origin git@github.com:<username>/app_name.git
    git push origin master-- upload files to remote server
    git push heroku-cedar master - push app to H (thefonso)


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