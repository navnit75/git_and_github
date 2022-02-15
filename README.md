# Git
* This repo Contains my rough notes for learning Git and Github, made while going through the below bootcamp. 
* Course Name: The Git and Github Bootcamp
* Course Duration: 17 hours 

# Certificate of Completion
- **(Just for my reference)** [Completion Certificate](https://udemy-certificate.s3.amazonaws.com/image/UC-48d5964c-a4db-459b-a652-835af3ccc754.jpg)


## Why GIT is needed? 
* Track changes across multiple files . 
* Compare changes of a project. 
* "Time travel" Back to old versions. 
* Revert back to previous versions. 
* Colloborate and share changes,
* Combine changes

## Git Vs Github
### Git
* Git is a version control software that runs locally on your machine. 
* We do not need to register for an account. 
* You don't need internet to use it . 
* You can use git without ever touching github.


### Github
* Github is a service that host git repo over cloud and makes it easier to collaborate with other people . 
* We need to signup. Its an online place to share work that is done using git. 


## Repositories
* A git workspace which tracks and manages files within a folder. 
* little encapsulation that keeps your all project files at a single place. With separate history. 
* We can have as many as repo as needed. 
* One defination we can say , the folder which usually contains the .git folder. 
* .git folder is used to store the file history of the repo. 
* WARNING! DO NOT INIT A REPO INSIDE OF A REPO
* i.e. Before running git init , use git status to verify that you are not currently inside a repo.

## Commit
* main job which git plays in a project, to keep the tally of the changes (can be made by you, or some one else).
* checkpoint in time , group the **changes** and give it a name
* Try to keep each commit on single thing (atomic things)
* Makes it easier to undo or rollback changes later on. 
* Makes code projector to easily review. 

## Ignoring Files using `.gitignore`
* We can tell GIT which files to ignore and directories to ignore in a given repository from tracking changes using a `.gitignore` file 


## Branches
* They allow us to coloborate such that each patch is provided the isolation it requires. 
* We can think of branches as alternative timeline. 
* They enable us to create separate context where we can try new thhings, and work on multiple idea at once. 
* If we work changes on one branch it won't impact the changes on other braches. 
* Later we can merge the branches together into main code base. 
* DEFAULT BRANCH: MASTER ( its like any other branch )
* People designate the master branch as their "source of truth" or the "official branch" it is left for us to decide. 


## Head
* Its a pointer that refers to the current location in your repository. 
* **Analogy**: `Its like book mark`. 
* If there are three person reading a book. 
* Then to know their reading location they will put three different book marks 
* But at a time only one person from one location can read, using one book mark. 
* So that is the HEAD pointer. 
* If I switch to some other branch then the head will point to the tip of that branch. 
* We can change the position to the HEAD pointer. 

