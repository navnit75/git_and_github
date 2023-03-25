# GITHUB
* It's a hosting platform for git repositories. 



## GIT CLONE
* To clone a repo , simply git clone <url> 
* git will retrieve all the files associated with the repo and copy to the local machine. 
* Full history of the repo would be provided as commits. 
* Make sure you are not already in git repo. 
```
git clone <url>.git
```

## GENERATING THE SSH KEY
* [Docs to generate SSH key ](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
* Usually its environment based better to get to the root of it . 

	
## LOCAL REPO --> GITHUB REPO

* Option 1: 
      * Create a new repo on Github
      * Connect your local repo ( add a remote )
      * Push up your changes to github

* Option 2: 
      * Create a brand new repo 
      * Clone it down to your machine 
      * Do some work locally 
      * Push up the changes to Github (using push command)

## REMOTE
* Before we can push anything to github we need to tell git about our remote repository on github. 
* We need to setup up a "destination" to push up to . 
* In git we refer to these destination as remotes. Each remote is simply an URL where hosted repo lives. 
* To view existing remotes for your repo, 
```
git remote 
   or 
git remote -v (verbose)
```
 
* Creating a remote
```
git remote add <name> <url> 
```
* Ex. 
```
git remote add origin https://github.com/blah/repo.git
```
* Origin is a conventional git remote name, but it is not special. 
* Any name can be given. 
* We can change it if we want. 
```
git remote add mygithuburl1 https://github.com/blah/repo.git
```

* Renaming a remote
```
git remote rename <old> <new> 
```
* Removing a remote
```
git remote remove <name> 
```
## PUSHING 
* Push all the changes in all the branches
```shell
$ git push <remote> 
```
* Pushing some work on git hub repo
* Here the `<remote>` denotes the Remote Repo
* Here the `<branch>` denotes the Local and Remote branch. 
* This will bringout a doubt ? Is it necessary that the Local and Remot branch needs to have the same name ? `NO`
```shell
$ git push <remote> <branch> 
```
* When security error comes 
```
Developer_settings > generate personal token > copy the personal token and use it in place of the password
```
* When we have different names scenerios or if we want to push the changes made on some local branch to different remote branch. 
```shell
$ git push <remote> <local branch> : <remote branch>	
```
* -u option of git push
* Running the git push -u origin master sets the upstream of local master branch so that it tracks the master branch on the origin repo. 
* So it mapped origin master of remote to the master of local . 
```
git push -u <remote> <branch> 
       or
   
git push -u <remote> <local branch> : <remote branch>
```

## ORIGIN
* This is a remote tracking branch.
* Reference to the state of the master branch on the remote. 
* Its like a bookmark pointing to the last known commit on the master branch on origin. 
* Remote tracking branch 
      * At the time you last communicated with this remote repository, here is where x branch was pointing. 
      * Follows a pattern 
```
<remote>/<master> 
```
* Listing all the remote branches 
```
git branch -r 	
```

## CHECKING OUT REMOTE
* Returning to the last pushed code. 
```
git checkout origin/main
```

## GITHUB-BRANCH
* By default my master branch is already tracking origin/master. 
* I didn't connect these myself.
* But situation arises what if there are other branches as well. 
* Remote branches such as origin/popsicles 
* What we will be do? How to connect 
* Super easy ? 
```
git switch <remote branch name> 
      or 
git checkout --track origin/puppies
```
* This makes a local puppies branch and sets it up to the track the remote branch origin/puppies. 


## GIT FETCH
* There could be a situation, in which a contributor adds the changes to the remote repo. 
* Meanwhile if someone working on local repo also make few changes. 
* At that situation we use fetch to get the changes, to a separate branch. 
* Only fetch the changes but not integerate it with working directory.
```
git fetch <remote> 
```
* git fetch origin will fetch all the changes from the origin repo. 
* Ex:
``` 
git fetch origin	
```
* To only fetch a specific branch 
```
git fetch <remote> <branch> 
```
* Getting the branch changes 
```
git fetch 
```
## GIT PULL
```
git pull = git fetch + git merge
```
```
update the remote changes from the remote repository
		+
update my current branch with whatever changes are on remote tracking branch. 
```
	
* Syntax
```
git pull <remote> <branch> 
```
* Ex: 
* This would fetch the latest information from the origin's master branch and merge those changes into our current branch. 
```
git pull origin master 
```
* Pull can result in MERGE CONFLICTS. 
* If I am on my local puppies(from the example) branch 
```
git pull
```
* pulls from origin/puppies automatically

      
## PUBLIC REPOS
* public repos are accessible 
* can be cloned


## ADDING CONTRIBUTORS
* settings > manage access : for adding contributors


## README.md
* Mark down : md
* Followed by github
* We can follow markdown tutorials
* [Markdown Tutorial](https://markdown-it.github.io/)
* Markdown in vs code (Ctrl + Shift + V : for Preview)


## GITHUB GISTS
* Github gists are a simple way to share code snippets and are useful fragments with others. 
* Gists are much easier to create, but offer far fewer feature than a typical Github repository. 

## GITHUB PAGES
* Github pages is a hosting service for static webpages, so it does not support server side code like python, ruby, or node. Just HTML/CSS/JS. 
* Name your static page index.html and use repo settings . 
```
Settings > Github pages > 
```

## PULL REQUEST
* Basically its a request by contributors for merging their feature into the Main branch. ( kind of merge request )
* They allow developers to alert team members to new work they need to be reviewed. 
* They provide a mechanism to approve or reject the work on a given branch. 
* They also help facilitate discussion and feedback on the specified commit. 
* WORK FLOW 
      * DO some work locally on a feature branch
      * Push up the feature branch to github
      * Open a pull request using feature branch just pushed up to github. 
      * Wait for PR to be approved and merged.

## RESOLVING PULL REQ LOCALLY
* If we choose to resolve pull req locally then the commands would be given. 
```
git fetch origin 
git switch my-new-feature
git merge master
fix conflicts
git switch master
git merge my-new-feature 
git push origin master
```
## CONFIGURING BRNANCH RULES
```
repo > settings > branch rules 
```
## FORKING
* Github allows us to create personal copies of other people repo. 
* We call these copies "fork" of the original . 
* Ability to fork is implemented by git
* WORKFLOW
```
1. FORK THE PROJECT
2. CLONE THE FORK
3. ADD UPSTREAM REMOTE
4. DO SOME WORK 
5. PUSH TO ORIGIN
5. OPEN PR
```
