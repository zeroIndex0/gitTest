### Testing out git
  
#### Push without setting up keys 
One thing that could help when pushing code using git is the command -c, followed by http.sslVerify=false. 
This will disable ssl verification for a single git command.  I cannot say for
certain about the security behind using this, but for someone first starting 
to wrap their head around git, it helps to push out a few things without 
starting down some rabbit holes right off the bat.  
```
git -c http.sslVerify=false
```
the command can be used for pulling, pushing, cloning, etc..
```
git -c http.sslVerify=false push origin master
```

  
#### Set a remote on a fresh folder
cd into your desired folder that you want to push to git.  
-Note: you must have a repo already created on github first-  
After you cd into the folder you want to create your remote on:  
```
git init
git remote add origin https://github.com/YOURUSERNAME/FORKED-REPO.git
```

After setting up the remote, you'll want to add files.  
You can check which files you want to add with:  
```
git status
```
The files you want to add will be in red.  To add them just type:  
```
git add filename
```
After everything is added, you'll want to commit your code so you can push it to github:  
```
git commit -m "Write Message Here"
```
Then is just a matter of doing the push step listed above:  
```
git push origin master
```
And if you need to push without setting up keys:  
```
git -c http.sslVerify=false push origin master
```

#### Setting a remote on a forked repo that was first cloned
If you clone a repository then decide to fork the repository a little while later,  
but want to keep your changes from when it was cloned, you need to change your  
remote.  It's not very common to clone then fork, but it can happen.  
Here is the command needed to update the remote.  

```
git remote set-url https://github.com/YOURUSERNAME/FORKED-REPO.git
```
Then you can check your remote with  
```
git remote -v
```
to verify it's pointing to your repository  

#### Accidentally ran git init in the wrong folder  
This is a fairly simple error to fix.  Remove the .git from the current folder.  
It will remove the (master) from the folder and you can start fresh afterwards.  
```
rm -rf .git
```
Try to keep in mind that this has a potential to be dangerous.  If you happen  
to hit enter before adding git, then you could delete everything and ruin your  
whole day.  So, just make sure you typed .git and not just .  
Now, if you started uploading some files first before you realized your mistake  
then you could be in for another set of problems, which involve failing to push refs.  
  
  


#### Fixing a 'failed to push some refs' error
Sometimes you might run into an error that reads something like "error failed to push some refs".  
It could be due to trying to push changes from different files you either moved from other  
folders or tried to rename a file to one you want to replace with the same name.  
You have to force a pull or rebase to fix this issue.  Forcing a pull seems to be safer, but  
could still be dangerous, so be careful.  
You might still need the -c http.sslVerify=false.  
So we could run one of the following commands:
##### WARNING:  
#### Back Up All Data Before Attempting  
#### I cannot stress enough about making sure ALL data in your working folder is backed up first
If you just ran an init on a new repo, but set the init in the wrong folder and had already  
uploaded some files, then this could be the solution to that problem.  You will have the  
failed to push some refs error due to git knowing the files are not coming from the same location.  
You can read up on this issue further by typing, in the command line:
```
git push --help
```
Then, searching for the section "notes about fast-forward".  
The section states that you can use a force push, but must know that you will lose history  
therefore making version control pointless.  This is okay if its a fresh repo and a lot less  
risky of a solution than the rebase method listed below this one.
```
git push --force origin master
```
After the first forced push, the error should clear and things should be realigned.  


If you create a new repo and want to push existing code to the new repo,
do not use the below method.  This method pulls what is already in the repo (I believe) and it will erase the data you currently have in your working folder 
with whatever is currently in the repo.  
Either start over, seek answers elsewhere, or add the files first through github then rebase.  
```
git -c http.sslVerify=false pull --rebase origin master
```
we have to pass in the remote and the branch for this to work, which is why we have origin master added.  
According to git, the 'rebase' functionality is to "Reapply commits on top of another base tip"  
Some say this is bad practice, but for the simple little repos trying to figure things out, it works.  


#### Removing Files And Folders:  
##### Files:
If you want to remove a file in git you can do it with the following command:  
```
git rm file-to-delete.extension  
```
Then, of course, commit and push the change.  
This will also remove the file from your filesystem.  
If you don't want to remove the file from your system and only from github you can use:  
```
git rm --cached file-to-delete.extension
```
Then, of course, commit and push the change.  
  
##### Folders:
Folders are similar with only one slight change to the command:  
```
git rm -rf folder-to-delete  
```
Then, of course, commit and push the change.  
The same as above, this will remove the folder from your filesystem.  
If you don't want to remove the folder from you system and only remove it from github you can use:  
```
git rm -rf --cached folder-to-delete
```
Then, of course, commit and push the change.
  
#### An important note about markdown files.  
Something that drove me nuts for far too long:
If you want to put a line break in your .md file then you need to put two spaces at the end of the line.  
I repeat:  
##### Two spaces at the end of a line will create a line break.  

Also, here is a [cheat sheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) when using markdown.  
  
Here is a [Reference](https://git-scm.com/docs) page for git
