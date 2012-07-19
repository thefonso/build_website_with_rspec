Git Cheat sheet - General commands

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




Configuration files:

    .gitignore (Edit this file to add files you want git to ignore.)

    .gitconfig (Edit this file to add custom aliases.)




More General git commands...

    git clone [url] (copies a remote git repo to local)

    git pull [server] [branch] (updates your local repo with server repo.)

    git remote add



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
    	
    	lp      	= log --pretty="format:'%h %ad | %an - %s%d'" --date=short
    	lgs     	= log --stat
    	ls      	= ls-files
    	fixup 	= commit --amend -C HEAD				
    	timeline = log --graph --branches --pretty=oneline --decorate
    	h = log --pretty=format:'%h - %an, %ar : %s'			
    	history = log --pretty=format:'%h - %an, %ar : %s'