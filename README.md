Testing out git

One thing that could help when pushing things using git is the command -c, followed by http.sslVerify=false. 
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


Sometimes you might run into an error that reads something like "error failed to push some refs"  
and its due to commits pushed while you were working locally.  You have to pull and rebase to fix this issue  
In our case we need the -c http.sslVerify=false.  
So we would run the following command:
```
git -c http.sslVerify=false pull --rebase origin master
```
we have to pass in the remote and the branch for this to work, which is why we have origin master added.  
According to git the 'rebase' functionality is to "Reapply commits on top of another base tip"  
Some say this is bad practice, but for the simple little repos trying to figure things out, it works.  
I could imagine though, if this were some large repo, this could cause some issues.  
  

#### An important note about markdown files.  
Something that drove me nuts for far too long:
If you want to put a line break in your .md file then you need to put two spaces at the end of the line.  
I repeat:  
##### Two spaces at the end of a line will create a line break.  

Also, here is a [cheat sheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) when using markdown.  
  
Here is a [Reference](https://git-scm.com/docs) page for git
