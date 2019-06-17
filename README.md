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
  
  


#### Fixing a 'failed to push some refs' error
Sometimes you might run into an error that reads something like "error failed to push some refs"  
and its due to commits pushed while you were working locally.  You have to pull and rebase to fix this issue  
In our case we need the -c http.sslVerify=false.  
So we would run the following command:
##### WARNING:  
#### Back Up All Data Before Attempting  
If you create a new repo and want to push existing code to the new repo,  
do not use this method.  This pulls and it will erase the data you have currently in your folder 
with whatever you currently have in the repo.  
Either start over, seek answers elsewhere, or add the files first through github then rebase.  
```
git -c http.sslVerify=false pull --rebase origin master
```
we have to pass in the remote and the branch for this to work, which is why we have origin master added.  
According to git, the 'rebase' functionality is to "Reapply commits on top of another base tip"  
Some say this is bad practice, but for the simple little repos trying to figure things out, it works.  

  
#### An important note about markdown files.  
Something that drove me nuts for far too long:
If you want to put a line break in your .md file then you need to put two spaces at the end of the line.  
I repeat:  
##### Two spaces at the end of a line will create a line break.  

Also, here is a [cheat sheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) when using markdown.  
  
Here is a [Reference](https://git-scm.com/docs) page for git
