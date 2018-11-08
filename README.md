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
  

#### An important note about markdown files.  
Something that drove me nuts for far too long:
If you want to put a line break in your .md file then you need to put two spaces at the end of the line.  
I repeat:  
##### Two spaces at the end of a line will create a line break.  

Also, here is a [cheat sheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) when using markdown.  
  
Here is a [Reference](https://git-scm.com/docs) page for git
