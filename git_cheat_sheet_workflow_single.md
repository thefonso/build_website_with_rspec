WORKFLOW - SINGLE user:

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

