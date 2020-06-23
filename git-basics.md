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

** eg:- **

**Step 1 :** Create accounts folder.  
**Step 2 :** Add `.gitkeep` file inside accounts folder.  
**Step 3 :** Run `git add accounts/`  
**Step 4 :** `git commit -m "Track accounts directory"`
