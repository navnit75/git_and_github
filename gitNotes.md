# GIT
## Documentation
[git docs](https://www.git-scm.com)

## Initial Configuration

* Configuring your username
```shell
$ git config --global user.name "Navnit Kumar" 
```

* Checking your username 
```shell
$ git config user.name
```
* Configuring your email
```shell
$ git config --global user.email "kumar.navnit4175@gmail.com"
```
* Checking your email 
```shell
$ git config user.email
```

## Basic Commands

* Info regarding current status of git repo
```shell
$ git status
```
* Initialization of repository.
```shell
$ git init
```
* WARNING! DO NOT INITIALIZE A REPO INSIDE OF A REPO
    * i.e. Before running git init , use git status to verify that you are not currently inside a repo.

## git add 
* WORKFLOW
```
/**********************************************************/
        Working Dir ( Place where we are working ) 
           |
           |
           v
        git add
           |
           |
           v
       Staging Area
           |
           |
           v
        git commit
           |
           |
           v
        Repository
/*********************************************************/
```

* Adding the files to the staging area
```shell
$ git add file1 file2
```
* to stage all the (modified)files at once
```shell
$ git add . 
```
## git COMMIT
* Committing the files for creating the checkpoint
```shell
$ git commit -m "my message" 
```
* Committing when you need to provide multiline messages to the commit. 
* Devops teams of the company follows a muliline commit rules , in which various jira tickets and other stuff are linked for reference. 
```shell
$ git commit 
```

* Staging all the changes of staging area as well as committing. 
```
$ git commit -am "<message>"
         OR
$ git commit -a -m "<message>"
```


## git LOG
* Retrives the information of commits
```shell
$ git log
```
* It will show an identifier for every commit called `commit hash`.

## Atomic Commits
* Keep your commits on single thing. 
* So that it is easier to roll back. 
* And it is easier to display changes. 
* Write the message , as if you are giving code base to change its behaviour
* make xyzz to frotz

## Changing the default editor of GIT
* This is for changing the default editor to VSCode
```shell
$ git config --global core.editor "code --wait"
```
* This is for changing the default editor to nano
```shell
$ git config --global core.editor "nano -w"
```
* This is for changing the default editor to vim
```shell
$ git config --global core.editor "vim"
```

## Log Tweaking
* Because sometimes the commit messages has to be big
* Shows first 5 character of commit hash.
```shell
$ git log --abbrev-commit
```
* Shows first 5 character of commit hash and one line message
```shell
$ git log --oneline 
```
* Shows full hash but one line message
```shell
$ git log --pretty=oneline
```
* Remember to keep the first line of commit message as summary of the whole commit message


## Amending Commits
* This only works if you have made mistake on `recent commit`.
* Suppose you have made some changes , but you realise there was some mistake in the commit message. 
* Or there was some modification extra modification required in one of the files. 
* As the commits are tracked and raising one more commit can elongate the process of commit getting merged. 
* As in `professional circle` there are code reviews which would be needed for the Code which has to be merged. 
* The process of , adding extra changes in the same commit is called `AMENDING`.
* Ammend the commit ( Text editor will open , with message provided )
```shell
$ git commit --amend
```

## .gitignore
* create a file called .gitignore in the root of repo.
* inside the file, we can write the patterns to tell git which files and folders to ignore. 
    * Ex. 
    * .DS_Store will ignore `files named .DS_Store`
    * `folderName/` will ignore an entire directory
    * .log will ignore any file with .log extension. 
* You need to commit .gitignore in every commit. 
* If there is any changes happens in the ignored files , the git will not cover. 

## Head
* To know where the head is pointing at 
```
$ git log 
```
* Check for HEAD -> master 

## git BRANCH
* To list the number of branches 
```shell
$ git branch
```
* The one which  is active will have "*" before the name. 

* Creating the new branch. This just creates the branch, it doesn't switch you to that branch. 
```shell
$ git branch <branch-name>
```
* Listing the branch information with the tip commit message
```shell
$ git branch -v 
```
## git SWITCH
* Used to switch branches. Branch name has to be perfect. 
```shell
$ git switch <branch_name> 
```
* Once switch and create commits. 
* We can see (master) written , in front the tip of master branch. 
* Meanwhile in front of the head commit ( new branch ) it will show a message of (HEAD -> <new_branch_name> )
* Creating branch and switching in one go
```shell
$ git switch -c <branch_name> 
```

## git CHECKOUT
* Another way of switching
```shell
$ git checkout <branch_name> 
```
* Old way to creating branch and switching into it 
```shell
$ git checkout -b <branch_name>
```

## What if we try to change branch, with changes in STAGING area?
* If we try to switch after modifying a file , it will give us an error. Saying the data would be lost, if we switch. 
* But instead of that if we added new file, it won't give any error. But the new file created would be in the staging area.


## delete BRANCH
* Deleting a branch. ( You cannot be on same branch which you are deleting. It will also give an error if branch we are deleting is not MERGED )
```shell
$ git branch -d <branch Name> 
$ git branch --delete <branch Name> 
```
* Deleting a branch without MERGING/FORCEFULLY: 
```shell
$ git branch -D <branch_name>
$ git brach --delete --force <branch_name>
```
## renaming BRANCH
* Change to the branch which you want to rename 
```shell
$ git branch -m <new_name> 
$ git branch --move <new_name> 
```

## Merge
* Merge operation is compilicated operation and required some flow knowledge. 
* There could be conflicts in the code. 
* One of the easiest and simplest variety of merge with no conflicts is , FAST FORWARD MERGE. 
* Example of fast forward is shown in above ASCII diagram. 
* Switch to destination branch. 
	* Ex: Branch a : Feature Branch
	* Action : I want to perform merge of Branch a to Master 
	* Switch to --> Master branch first , then run `git merge a`
```
$ git switch master
$ git merge <branch_name> 
```
## Fast Forwarding MERGE
* Before Merging 
```     
      <Master>
## ----> ##
         |
         |
         +-------->##---->## <Head>
     <BugFix>
```     
* After merging

```     
## ----> ##
         |		 <Head> 
         |              <bugfix>
         +-------->##---->##
     			<master>
```   				
* When the one of the branch have  more number of commits then the master branch. 
* So when merge takes place, master pointer moves to the head of the branch with which it is merged. 
* One of the simplest of the merges. 

## Recursive MERGE
* Now this variety of merge is also optional when there is no conflicts. 
* If we have file say a. It has some content
* If we append the data to that file and add(edits) into new branch by providing different commit names.  
* And master branch forwards by creating new file b. (but not editing the file a ).
* As we can see , we are creating a scenerio , that further commits are just appending the data to the files in the consideration, or we are adding a new file itself.
* In this situation conflict doesn't occur. 
* As the conflict doesn't occur ---> Merge happens simply.  

* Before Merging 
```   
              <Master>
## ----> ##---->##
         |
         |
         +-------->##---->## <Head>
                         <BugFix>
```     
* After merging
```
                 (Parent-1)   (merge commit)
## ----> ##------->## ----------------->##
         |		 <Head>         ^ 
         |              <bugfix>       /
         |			      /
         +-------->##---->##---------
     	                (Parent -2)	
```      
     

*Git creates an  addittional commit with two parent commits.
*After we provide with 
```shell
$ git merge <branch name> 
```
* It will automatically open text editor for inputing the message for commit. 


## Conflict
* As we type the command 
* A warning message would be shown regarding the conflict. 
```
git merge <branch_name> 
```
* I would be taken to the defautl editor, where it would highlight the conflict. 
* I would keep the content I would like to keep and I would delete the content I would like to delete. 
* I would commit using the new file created, by removing the conflicts. 


## git DIFF
* Without additional options, git diff lists all the changes in our working directory that are not staged for the next commit. 
* Basically you compare your before the edit version of file, to the edited version. 
* For each comparison the git tells which file it is comparing. Usually these are two verisons of the same file.
* Git also declares them as A and B
* Second line tell about the meta data
* Markers  
    * file A gets '-' sign
    * file B gets '+' sign
* Chunks : 
    * Git is not going to show us the entire files 
    * Git shows the little context and changes.
    * Red and green color represents changes.

* Header contains some number: 
    * -3,4 to +3,4
    * '-' represents file a. (old file)
    * from line 3 , four lines.
    * '+' represents file b. (new file)

* git diff lists all the changes in our working directory that are not staged for the next commit. Basically whatever we have newly added in the file, after the last commit. 
* But if its in the staging area , it will show blank. 
```shell
$ git diff
```
* git diff HEAD lists all changes in the working tree since your last commit. 
* if any file is displayed as /dev/NULL then it was not there in the previous commit.
* if the changes in present working tree either staged or unstaged, it will show the difference with last commit.  
```
$ git diff HEAD
```


* to find out the difference between the staged area and the last commit. 
```
$ git diff --staged 
 	or 
$ git diff --cached
```
* Narrowing down the files to specific files. 
* From last commit to specific file in STAGING area. 
```
$ git diff --staged filename1 filename2.....
```
* From last commit to present working tree (Staged or non staged )
```
$ git diff HEAD filename1 filename2....
```
* Comparing the changes from two branches
```
$ git diff branch1..branch2
    or 
$ git diff branch1 branch2
```
* Comparing the changes from two branches, but for specific files. 
```
$ git diff branch1 branch2 filename
```
* DO remember the file a: will represent file from branch1 and b; represent file from branch2
* Flipping the branches also flippes the change representation

* Comparing the changes between the two commits 
```
$ git diff commit_hash1..commit_hash2
```

## Stashing
* Scenerio , if you are working on something and suddenly you want to revert back to previous commit. 
    * My changes come with me to the destination branch. [ Happens only when there are no conflicts]
    * Git won't let me switch if it detects potential conflicts. [ When there are conflicts ]

* its a super useful command that helps you save changes that you are not yet ready to commit.
* You can stash changes and come back from them later. 
* Running git stash will take all the uncommitted changes (staged and unstaged) and stash them, reverting the changes in your working copy. 
```
$ git stash 
   or 
$ git stash save
```
* To remove most recently stashed changes in your stash and reapply them to your working copy. 
```
$ git stash pop 
```
* If we want to apply whatever is stashed away, without removing it from the stash. 
* This can be useful if you want to apply stashed changes to multiple branches. 
```
$ git stash apply
```
* Can add mulitple stashes into stack of stashes. They will all be stashed in the order you added them. 
```
$ git stash 
// Do something here
$ git stash 
// do something 
$ git stash
```
* listing the stashes
* It will tell the commit at which we have stashed the changes.
```
$ git stash list
```
* Applying specific stashes 
* By default it will apply, the most recent changes.
```
$ git stash apply <stash-id> 
Ex. 
$ git stash apply stash@{2}
```
* Dropping stashes 
```
$ git stash drop <stash-id> 
```
* Completely clearing the stash
```
$ git stash clear
```

## Rolling back to previous COMMITS
* We can roll back to previous commits 
```
$ git checkout <commit hash> 
```
* reverting back to present head 
```
$ git switch <branch_name you want to switch> 
```
* You can create another branch if you want to merge the changes 
```
$ git switch -c <branch_name> 
```
* GIT CHECKOUT supports another syntax as well: HEAD reference
* Refers to commit before HEAD(parent)
```
$ git checkout HEAD~1 
```
* Refers to 2 commits before HEAD
```
$ git checkout HEAD~2
```
* Switching to previous commit
```
$ git switch -
```


## Restoring back the changes

* Supppose we edited the files , now we want to go back the (without edited version of the file )
* We can do that by , undoing the change ( deleting whatever we have changed ) 
* Note that this command is undoable , and will remove any changes you have made on the file. 
* If changes are important COMMIT the changes. 
* OR 
```
$ git checkout HEAD <filename> 
        or
$ git checkout -- <filename> 
	or 
$ git restore <filename> 
```
* git restore using HEAD reference options
```
$ git restore --source HEAD~1 <filename>
```
* removing files from STAGING area. 
```
$ git restore --staged <filename>
```

## git RESET     
* We can revert back to commits , and delete all the previous ones. 	
* But changes wouldn't be modified. 	
```
$ git reset <commit_hash> 
```

## git HARD RESET
* We can use this to undo till the <commit whose hash we have provided>
* And all the corresponding we did till that commit.
* BE VERY CAREFUL 
```shell 
git reset --hard <commit-hash> 
    or 
git reset --hard <head reference using "~" approach> 
```

## Reverting
* git revert is similar to git reset in that both "undo" changes, but they accomplish it in different ways. 
* git reset actually moves the branch pointer backwards eliminating commits.
* git revert creates a brand new commit which reverse/undos the changes from a commit. Because it results in a new commit, you will be prompted to enter a commit message.
* git restore we are talking about, after we have done changes , if we do git restore <commit_hash> it will create a new changes
*  Scenerio like " i want to undo the changes, but I want to keep the record of commit" 

*  Here I have reverted the changes, but instead of deleting commits, I have kept the commits and created a new commit with the changes 
*  or We use the git revert to reverse the same commits as before, by adding new commit to the chain. 
*  There may also arise various conflicts
git revert <commit-hash> 

## Situation based diff. B/W Revert and Reset 
* Situations to use revert : 
    * If you want to reverse some commits that other people already have on their machines, you should use revert. 

* Situations to use reverse: 
    * If you want to reverse commits that you haven't shared with others, use reset and no one will ever know 




## git REBASING
* Dangerous
* Concatenates the feature branch with the master branch , such that the entire feature branch begins at the tip of master branch . 
* All of the work is still there, but we have re-written history. 
* Instead of using a merge commit , rebasing rewrites history by creating new commits for each of the original feature branch commits. 
```
git switch feature
git rebase master
( concatenate feature branch , with master )
```
* Never rebase commits that have been shared with others. If you have already pushed commits up to github.. do not rebase then unless you are positive no one on the team is using those commits
* Aborting a rebase 
```
git rebase --abort ( in case of conflict )
```

### Rebase Workflow
* try to rebase
* conflict detected
* resolve conflict 
```
git rebase --continue ( to continue the rebase ) 
   or 
git rebase --abort
```
## Interactive Rebase
* Here we are basically recommitting the commits. 
* We need to specify the range till we want to edit. 
```
git rebase -i HEAD~4
```
* In our text editor, we'll see a list of commits alongside a list of commands that we can choose from. 
* `The order of commits would be reversed. As in the newest commit will at downmost line , and oldest commit would be in uppermost line.` 
* Commands are executed through reversed order itself. 
```
pick - use the commit
reword - use the commit , but edit the commit message
edit - use commit, but stop for amending 
fixup - use commit contents but meld it into previous commit and discard commit message
drop - remove commit
```

* REWORD : We are changing the commit message here. 
    * Using reword
    * After editing the command, we will be saving the file and closing the file. 
    * Just after that another file will open specifying the, change which we want to do. 

* FIXUP : We are merging the various commits into single commit. 
    * Using fixup 
    * You meld the change to the previous commit, so you always need to select the commit which is done recently.
    * In the sense we would be using command on the commit , which would be at below position in the two which you want to meld. 
    * Do remember the commit message kept would be of the second commit.---> This is not imp. as you can again change the commit message. 
* DROP : Completely remove the Commit (with the changes)
```
pick 1d09bac add project files
pick 49596b6 add basic HTML boilerplate
pick a1757ff add bootstrap
pick f0651dc add top navbar<----------------,
fixup 1fbe2ee fix navbar typos--------------|
fixup 65b6096 fix another navbar typo-------'
pick fc67645 my cat made this commit
pick 130a9eb Create README.md
```



## git TAGS
* Sticky note on commit
* Two types of tags
    * Lightweight tags : name/label pointing to a particular commit. 
    * Annoted tags: store extra meta data including author's name and email, date and a tagging message ( like a commit message )


* Semantic Versioning
```
2   .   4    .    1
Major	Minor    Patch 
      release
```
* First release 1.0.0
* Patches generally do not contain new features or significant changes. They typically signify bug fixes and other changes that do not impact how the  code is used. 
* Minor  signify a new features or functionality have been added, but the project is still backwards compatible. 
* No breaking changes. 
* Major releases signify significant changes that is no longer backward comapatible. Feature may be removed or changed subtantially. 
* Viewing Tags
```
git tag
```
* Searching for tags which matches particular version by passing wildcard pattern. 
* This command list all the tags which have beta in them
```
git tag -l "*beta*"
```
* All tags which starts with 17
```
git tag -l "17*"
```
* Move around tags 
```
git checkout v2.2.2
```
* Playing around git diff , to know the difference between two versions
```
git diff v2.2.0 v2.2.1
git diff v2.2.0..v2.2.1
```
* Creating lightweight tags
    * This will reference the HEAD pointer at the time we are putting this command
```
git tag <tagname> 
```
* Creating annotated tags
    * Here new file will open in the editor
```
git tag -a <tagname> 
```
* Know the messasges added in the tag
```
git show v1.1.1
```
* Tagging previous commits using Lightweight tags
```
git tag <tagname> <commit> 
```
* Tagging Older commits by their commit hash 
```
git tag -a <tagname> <commit hash>
```
* All the tags are unique and we cannot use any tags twice but we can do that forcefully
``` 
git tag <tagname> <commit hash> -f 
```

* Delete a tag
```
git tag -d <tag_name>
```

* By default when we push the changes to the remote repo, the tags are not going to be included. 
```
git push <remote> --tags
```
* Single tag push 
```
git push origin v1.5
```

## .git FOLDER
* Configure the local user name
```
git config --local user.name "<username>"
```
* Configure the local email 
```
git config -- local user.email "<email>"
```

* We can change the color of various aspects of git terminal using the config file provided in the git config folder. 
```
[color]
	ui = true
[color "branch"]
	local = cyan
	current = yellow bold
[color "diff"]
	old = magenta bold
```
## Hashing Function

[Deep Dive Slide](https://www.canva.com/design/DAEV-h9bSG4/R6FyldDe8CO8Wfn8z92yRA/view?utm_content=DAEV-h9bSG4&utm_campaign=designshare&utm_medium=link&utm_source=sharebutton#35)

* Map input data of arbitary size to fixed size output values. 

* Cryptographic hash functions: 
    * One way function which is feasible to invert. 
    * Small change in input yields large change in the output. 
    * Deterministic - same input yields same output. 
    * Unlikely to find 2 outputs with same value. 

* Git uses a hashing function called SHA -1 
* It generated 40 digit hexadecimal number. 

* Taking some data and generating the hash (unique key) that would be used to store our object. 
```
git hash-object <file> 
```
* Ex
    * Hashing the stdin file . 
```
echo "hello" | 	git hash-object --stdin
```

* Telling git to actually store the provided file with provided hash 
* Put a -w flag on the git hash-object command
* To realise this demo you can check the content of .git/object. 
```
git hash-object <file> -w
```
* Ex
    * Hashing the stdin file. 
```
echo "hello" | git hash-object --stdin -w
```
* Retriving the stored file using hash function 
```
git cat-file -p <object hash (full / first five letters)> 
```
* In the .git/object folder. The file object would be saved in folder named by first two letter of the hash produced. and other 38 letters name the object inside that file. 

* BLOBS: Binary Large Object, ( set of multiple object )
    * They do not even include the filenames of each file or any other data. They store the content of the file. 
    * The files stored in the .git/object folder are the BLOB
    * They are building block of the way it works 

* Trees: 
    * Trees are git objects used to store the contents of the directory. 
    * Each tree contains a pointer that can refer to blobs and to other trees. 
    * Each entry in a tree contains the SHA - 1 hash of a blob or tree, as well as mode, type and filename. 
* Ex. 
```
Folder 
|
'--File1.txt
```
* We will have one tree , and one blob
* Tree pointer would be pointing to the blob
* To see a tree of a commit hash, or a tree hash 
```
git cat-file -p <tree hash/ commit hash> 
```
```
              root tree
   index.html/ \      \ styles
	    / main.js  \
          blob    \    tree
                 blob  /   \ nav.css
		      /     \
	      app.css/       \ 
	            blob    blob
```		    
* In an existing repo we can see trees. 
```
git cat-file -p master^{tree}
```

* If we take a tree hash 
```
git cat-file -t <tree hash> 
```
* Commit object contains a tree object along with information about the context that led to the current tree. 
* Commit store reference to parent commit(s), the author, the committer, and of course the commit message.


## git REFLOG
* Git usually keeps a record of when the tips of branches and other references were updated in the repo. 
* We can view and update these reference logs using the git reflog command. 
* It stores all the event , in which our HEAD changes. 
* Location: .git/logs/HEAD 

* Every branch HEAD are also logged. 
* Location: .git/logs/refs/head
* Location: .git/logs/refs/remotes

* Limitation: 
    * reflogs are local, if I am cloning some directory I would not be recieving their reflogs. 
    * reflogs would be storing only my particular reflog. 
    * Reflogs are not permanent , git cleans out old enteries around 90 days, though this can be configured. 


* COMMAND

    * Used to show every movement of HEAD in the repo,
```
git reflog show HEAD
```
* Some conventions
```
HEAD@{0} -- Recent entry
HEAD@{78} -- Earliest entry
```

* reflog can also be used to trace out the logs of other branch tip as well 
```
git reflog show <branch name>
```
* to check the head movement 10 moves ago in reflog
```
git reflog show HEAD@{10}
```
* to check the head movement 2 moves ago in reflog
```
git checkout HEAD@{2}
```
* to check the difference
```
git diff HEAD@{0} HEAD@{5}
```
### Timed Reference
* Every entry in the reference log has a timestamp assosiated with it. 
* We can filter reflogs enteries by time/date by using time qualifiers like . 
```
1.day.ago
3.minutes.ago
yesterday
Fri,12 Feb 2021 14:06:21 -0800
```
* Ex.
```
git reflog master@{one.week.ago}
git checkout bugfix@{2.days.ago}
git checkout master@{1.week.ago}
git diff main@{0} main@{yesterday}
git diff HEAD@{0} HEAD@{yesterday}
```
## Undoing stuff using REFLOG
* Suppose a condition in which I have hard reset some commit . 
```
git reset --hard <commit hash> 
```
* There is no way we are getting to that commit. 
* Workflow would be something like
```
git reflog show master 
      or 
git reflog show HEAD
```
* We can now know the commit hash to which we want to revert back to
```
git checkout <commit hash> 
```
* Bascially what hard reset does, it deletes the parent commit and child commit or specified commit. 
* So the commit which we believe , have resetted or deleted is still there in the .git/object but not connected. 
* So to again revert back the changes what we can do 
```
git reset --hard master@{1}
```
```
: master@{1}  
```
* is quantifier which we really want to revert back to .
	
### undoing REBASE
* After doing rebasing 
* If you have edited say 5 commits
```
git reflog show <branch_name> 
```
* Will show all the 5 commits, with the quantifier branch_name@{num}
* If you all of the changes undone choose the , last(earliest commited one) commit from the group of 5. 
```
git reset --hard <commit_hash> 
        or 
git reset --hard branch_name@{num}
```
### UNDOING the UNDOING
* Now we undid the changes
* Later we realized , oh the changes we were perfect. 
* We can again revert back by going through the reflog. 

## Custom git aliases
* Global config file is kept at 
```
LINUX: ~/.gitconfig
or 
~/.config/git/config. 
```
* Any configuration we change in the file will be applied across all the git repos. 
* We can also alter configuration variables from the command line if preffered. 
* Setting the parameters with the --global tag
```
git config --global user.name
git config --global user.email 
```
* Aliases make git easy. 
* Instead of typing git status -> git s 
* Instead of typing git commit -> git ci
* Instead of typing git log -> git lg 

* Appending these lines in the global config would do the job. 
```
[alias]
	s = status
	l = log
```	
* We can do the same thing from command line as well 
```
git config --global alias.showmebranches branch
```

* For parameterized aliases 
```
[alias]
	s = status
	l = log 
	cm = commit -m 
```
* So we will be able to use 
```
git cm "commit message here"
```
* Here cm acts like macro for commit -m, --> wherver cm comes it would be replaced by commit -m 

### Useful links to the git aliases
* [Git Alias Repo](https://github.com/GitAlias/gitalias)
* [Extending Functionality](https://www.durdn.com/blog/2012/11/22/must-have-git-aliases-advanced-examples/)
* [Git Alias Gist](https://gist.github.com/mwhite/6887990)
