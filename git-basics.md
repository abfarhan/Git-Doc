# **Git Document**

## **To initialize a git repository**

```
 git init
```

## **To add the changes of all the files in the current directory(folder) to staging area**

```
 git add .
```

## **To commit the changes to the repository with message**

```
 git commit -m "initial commit"
```

### commit message best proctice

 - A short single line summary( less than 50 char)
 - Optionally followed by a blank line and a more complete description.
 - keep each line to less than 72 chars.
 - Write commit message in present tense, not past tense.

## **To view the commit log**

```
 git log
```

 - `git log -n 5` :- Shows the `5` recent commits
 - ` git log --grep="init" ` :- Shows the commits that has `init` in the commit message.
 - `git log --grep="fix"` :- Shows the commits that has `fix` in the commit message

## **To see the file difference b/w working directory and repository**

```
 git diff
```

Is used to see the changes that we made to the file. The difference between the file in our working directory and the file in the repository.

## **To view the changes in the file of staging area and the file in the repository**

```
 git diff --staged
```

 - `git diff --cached ` :-  Also works. `--cached` is another alias for `--staged`.
 - `git diff --color-words` :- This will show the only the words that we changed in different color.

## **To delete a file**

### **To delete a file there are 2 ways.**

**Method 1 :-**

First delete the file manually and give the below git command to remove it from staging area.

```
 git rm <file name>
```

**eg:**  `git rm file_to_delete1.txt`  

 Now because we deleted the file manually, the above git command will only remove it from staging area.

**Method 2 :-**

Execute the below command, 

```
 git rm <file name>
```

`eg:-  git rm file_to_delete2.txt`  

Now because we did not deleted it manually, the above command will delete the file and removing from staging area.

## **To rename a file**

**Method 1:-**  

Rename it manually, then if you run `git status` command we will see a file is deleted and new file is added. So we need to run the below commands,

```
 git add <new file name>
 git rm <old file name>
```

Now again if run the `git status` command we will see the file is renamed.

**eg:**  

`git add file1.txt`  
`git rm first_file.txt`

**Method 2:-**

Execute below command  

```
 git mv <old file name> <new file name>
```

**eg :**  `git mv second_file.txt file2.txt`  

Now if we run `git status` we will see that the file is renamed.

## **To move a file to another folder**

**Method 1:-**  Moving it manually, then execute below command,

```
 git rm <file name>
 git add <folder name>/<file name>
```

**Method 2:-** Execute bolow command

```
git mv <file name> <folder name>/<file name>
```

**eg:-** `git mv third_file.txt first_folder/third_file.txt`

## **To commit everything without staging**

```
git commit -am "<Commit message>"
```
--- or ---

```
git commit -a -m "<Commit message>"
```

**eg:-**

`git commit -am "Edits PIN code throughout website"`  

`git commit -a -m "Edit PIN code throughout website"`

## **To see the changes in a particular commit**

```
 git show <git commit id (SHA)>
```

we can give either the entire SHA or the first 6 to 8 characters. SHA(Hash value).

**eg :-**  `git show 3781b902`

If you don't remember the commit id run `git log` it will show all the commits with commit id.

## **To compare two commit changes**

```
 git diff <SHA of one commit>..<SHA of another commit>
```

**eg :-**  

`git diff a67911bae..0067a177c`

`git diff a67911bae..0067a177c --color-words`

## **To give multi line comment**

Run the below commit command without message,

```
git commit -a
```

Now an editor will open asking for the commit message. In first line of commit message give the message heading, the leave an empty line, in the third line write the message description. Then close the editor.

## **To see the commit log with only commit message**

```
 git log --oneline
```

## **To discard the changes in the working directory**

```
 git checkout -- <file name>
```

**eg :-**

`git checkout -- index.html` : Discards the changes in index.html

`git checkout -- .` : Discards the changes of all file.

## **To Unstage files**

```
 git reset HEAD <file name>
```

**eg :-**  `git reset HEAD tours.html`

## **To add new staged changes to the last commit.**

First add the new changes to the staging area using the command `git add <file name>` , then run the below command,

```
 git commit --amend -m "commit message"
```

**eg:-** `git commit --amend -m "Reorder recommended items for trip"`  

So here `amend` tell to bring back whatever in the last commit to staging area, add whatever new changes in the staging area with it and recommit back.

Even if you want to change the commit message of the previous commit use the same command with different commit message.

```
 git commit --amend -m "new commit message"
```

**Note** :- Instead of amend try soft reset.

## **To retrieve old versions (To revert commit)**

```
 git checkout <SHA of the previous commit that we want to revert back to> -- <file name>
```

Now make changes to the file and add it to the staging area. And then commit it.

## **To revert commit**

```
 git revert <SHA of the commit that we want to revert>
```

Now the editor will open saying the details like `Revert "<message of the reverting commit>"` and `This reverts commit "<SHA of the reverting commit>"`

## **To remove untracked files**

If you run `git clean` it will show 3 options `-i`, `-n` and `-f`.

 - `-n` means it will show you what will happen if you run the command. `git clean -n`
 - `-f` means forces the command to execute and remove the untracked file. `git clean -f`

## **To ignore some files from tracking use .gitignore file**

Create a `.gitignore` then add the name of the file that we want to ignore in the `.gitignore` file.

## **To ignore tracked file**

If we want remove tracked file from repository but don't want to remove it from working tree but want to ignore it then,

```
 git rm --cached <file name>
```

Then add the file name in the `.gitignore` file and commit it.

**eg:-**

Run the command `git rm --cached .vscode/settings.json`  

Now in `.gitignore` file add `.vscode/settings.json` and then commit it.

## **To track empty directory**

To track an empty folder add `.gitkeep` file inside that folder. Then add the folder to staging area and then commit.

**eg:-**

**Step 1 :** Create accounts folder.  
**Step 2 :** Add `.gitkeep` file inside accounts folder.  
**Step 3 :** Run `git add accounts/`  
**Step 4 :** `git commit -m "Track accounts directory"`

## **To find ancestry commits**

### To find parent of HEAD
HEAD will be pointing to final commit.

 `git show HEAD^`  

 `git show HEAD~` or `git show HEAD~1`

### To find grandparent of head

 `git show HEAD^^`  

 `git show HEAD~2`

### To find great grandparent of head

 `git show HEAD^^^`  

 `git show HEAD~3`


### To find parent of a commit

 `git show <SHA>^`  

 `git show <SHA>~` or `git show <SHA>~1`

 **eg :-**

 `git show deff01qw^`  

 `git show deff01qw~` or `git show deff01qw~1`

## **Tree listing**

```
 git ls-tree HEAD
``` 
 This will list the directories and files at the point of latest commit where the head is pointing to.

## **Filtering commit log**

`git commit -3` :- Shows the last 3 commits.

`git commit --since=2020-06-01` :- Show every commits from that date (yyyy-mm-dd).

`git log --until=2020-06-21` :- Shows every commit untill that date.

`git log --author="<author name>"` :- Shows all the commits made by that author.

`git log --until="3 hours ago"` :- Shows commits made untill 3 hours ago.

`git log --until="3 days ago"` :- Shows commits made untill 3 days ago.

`git log --grep="<regular expression>"` :- Shows commit matches that regular expression.

`git log --grep="<commit message>"` :- Shows commits that matches the commit message.

`git log <file name>` :- Shows all the commits made of that file. ( `git log course.html` )

`git log <SHA>..<SHA>` :- Shows all the commits inbetween the SHA(commit id) value.  

For more run the command `git help log` .

## **To list the branches**

```
 git branches
```

## **To create a branch**

```
 git branch <branch name>
```

A branch name can contain only letters, numbers and underscore ( `_` ).

## **To switch branch**

```
 git checkout <branch name>
```

## **To create and switch new branch**

```
 git checkout -b <branch name>
```

This will create a new branch and swich the HEAD to that branch.


## **Compare branches**

```
 git diff <branch 1>..<branch 2>
```

## **To see the branches that are merged**

```
 git branch --merged
```

`git branch --no-merged` :- this will show the branches that are not merged.

## **Renaming the branch**

When we are in a branch and we want to rename current branch then,

```
 git branch -m <newbranch>
```

If we are in a branch and we want to rename another branch then,

```
 git branch -m <oldbranch> <newbranch>
```

## **Delete branches**

```
 git branch -d <branchname>
```

## **Reset branches**

### **Soft reset**

 - Moves the head pointer.
 - Does not change the staging index.
 - Does not change the working directory.

```
 git reset --soft <tree-ish>
```

Soft reset is most useful when we want back thing up in the commit timeline and then recommit it again.

### **Mixed reset**

 - Moves the head pointer.
 - Changes staging index to match the repository.
 - Does not change the working directory.
 - Default choice. If we use `git reset` without `--mixed` it does the same thing.

```
 git reset --mixed <tree-ish>
```

### **Hard reset**

 - Moves the head pointer.
 - Changes staging index to match the repository.
 - Changes working directory to match the repository.

```
 git reset --hard <tree-ish>
```

## **Merge code**

If we are on the branch that we want to recieve it then,

```
 git merge <branch name>
```

eg:- If we want to merge branch1 to master branch, then first go to the master branch `git checkout master` and then `git merge branch1`.

## **Save changes in the stash**

```
 git stach save "<stash name>"
```

## **View stached changes**

```
 git stash list
```

This will show the list of stash that we made.

### To see the stat of perticular stash

`git stash show stash@{0}` :- Here stash@{ `0` } is the the stash position. Run `git stat list` to list the stash and to get the position of a perticular stash.

### To see the code changes of a perticular stash

`git stash show -p stash@{0}` :- Here stash@{ `0` } is the the stash position. Run `git stat list` to list the stash and to get the position of a perticular stash.

## **Retrieve stashed changes**

```
 git shash pop stash@{0}
```

```
 git shash pop stash@{0}
```

Here stash@{ `0` } is the the stash position. Run `git stat list` to list the stash and to get the position of a perticular stash.

If there is only one stash then simply run `git stash pop` or `git stash apply`

 - `pop` : Applies to the working directory and removes from stash list.
 - `apply` :  Applies to the working directory but does not removes from stash list.

## **Delete stashed changes**

```
 git stash drop stash@{0}
```

Here stash@{ `0` } is the the stash position. Run `git stat list` to list the stash and to get the position of a perticular stash.

If there is only one stash then simply run `git stash drop`.

If there are multiple shash in the stash list and we want to delete everything the run `git stash clear` .

## **Remote branch**

### To see remote branch

`git branch -r`


### To see remote branch and local branch 

`git branch -a`

## **Pushing changes to the remote repository**

If we are pushing the changes for the first time or if our branch is not tracked,

```
 git push -u origin master
```

Here -u tells to track the local branch with remote branch. In this case local branch master with remote branch master.  

Once our branch is tracked then, `git push` . If we cloned the repository using git clone then it will be tracked by default.

## **Fetch changes from remote repository**

```
git fetch
```

If we have more than one remote branch the we have to specify it, for eg: `git fetch origin` .

## **Merge in fetched changes**

```
 git merge origin/master
```

## **git pull**

The combination of fetching and merging is pull.

`git pull` =  `git fetch` + `git merge`

## **Delete a remote branch**

```
git push origin --delete <branch name>
```

We can also do `git push origin :<branch name>` to delete a remote branch.

Both of the above command will delete the tracking branch as wll as remote branch, but we will have that branch in our local repository. 

## **Collabration workflow**

#### Person1

> $ `git checkout master`  
> $ `git fetch`  
> $ `git merge origin/master`  
> $ `git checkout -b feedback_form`  
> $ `git add feedback.html`  
> $ `git commit -m "Add customer feedback form"`  
> $ `git fetch`  
> $ `git push -u origin feedback_form`   


#### Person2

> $ `git checkout master`  
> $ `git fetch`  
> $ `git merge origin/master`  
> $ `git checkout -b feedback_form origin/feedback_form`  
> $ `git log`  
> $ `git show sdfn23ensd`  
> $ `git commit -am "Add tour selector to feedback form"`  
> $ `git fetch`  
> $ `git push`  


#### Person1

> $ `git fetch`  
> $ `git log -p feedback_form..origin/feedback_form`  
> $ `git merge origin/feedback_form`  
> $ `git checkout master`  
> $ `git fetch`  
> $ `git merge origin/master`  
> $ `git merge feedback_form`  
> $ `git push`  
