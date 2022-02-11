# Git
* This repo Contains my rough notes for learning Git and Github, made while going through the below bootcamp. 
* Course Name: The Git and Github Bootcamp
* Course Duration: 17 hours 

# Certificate of Completion
- **(Just for my reference)** [Completion Certificate](https://udemy-certificate.s3.amazonaws.com/image/UC-48d5964c-a4db-459b-a652-835af3ccc754.jpg)


## WHY GIT IS NEEDED? 
* Track changes across multiple files . 
* Compare changes of a project. 
* "Time travel" Back to old versions. 
* Revert back to previous versions. 
* Colloborate and share changes,
* Combine changes

## GIT AND GITHUB DIFFERENCE
### GIT
* Git is a version control software that runs locally on your machine. 
* We do not need to register for an account. 
* You don't need internet to use it . 
* You can use git without ever touching github.


### GITHUB
* Github is a service that host git repo over cloud and makes it easier to collaborate with other people . 
* We need to signup. Its an online place to share work that is done using git. 


## REPOSITORIES
* A git workspace which tracks and manages files within a folder. 
* little encapsulation that keeps your all project files at a single place. With separate history. 
* We can have as many as repo as needed. 
* The folders which usually contains the .git folder. 
* .git folder is used to store the file history of the repo. 


## NESTED REPOS ( DOUBT SOLVING )
* If we have folders nested inside a git repo. 
* WARNING! DO NOT INIT A REPO INSIDE OF A REPO
* i.e. Before running git init , use git status to verify that you are not currently inside a repo.

## COMMIT
* checkpoint in time , group the changes and give it a name
* Try to keep each commit on single thing 
* Makes it easier to undo or rollback changes later on. 
* Makes code projector to easily review. 

## IGNORNING FILE USING .gitignore
* We can tell GIT which files to ignore and directories to ignore in a given repository
* using a .gitignore file 


## BRANCHES
* They allow us to coloborate such that each patch is provided the isolation it requires. 
* We can think of branches as alternative timeline. 
* They enable us to create separate context where we can try new thhings, and work on multiple idea at once. 
* If we work changes on one branch it won't impact the changes on other braches. 
* Later we can merge the branches together into main code base. 
* DEFAULT BRANCH: MASTER ( its like any other branch )
* People designate the master branch as their "source of truth" or the "official branch" it is left for us to decide. 


## HEAD
* Its a pointer that refers to the current location in your repository. 
* Analogy: Its like book mark. 
* If there are three person reading a book. 
* Then to know their reading location they will put three different book marks 
* But at a time only one person from one location can read, using one book mark. 
* So that is the HEAD pointer. 
* If I switch to some other branch then the head will point to the tip of that branch. 
* We can change the position to the HEAD pointer. 

## LINKS TO CHECKOUT
[Git Intro : Colt Steele](https://www.canva.com/design/DAETQyFE6pM/mLt1oYF8gP_mqBS3ghb-BA/view?utm_content=DAETQyFE6pM&utm_campaign=designshare&utm_medium=link&utm_source=sharebutton#59)



