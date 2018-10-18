Testing out git

One thing that could help when pushing things using git is the command -c
This will disable ssl verification for a single git command.  I cannot say for
certain about the security behind using this, but for someone first starting 
to wrap their head around git, it helps to push out a few things without 
starting down some rabbit holes right off the bat.
I digress, this will disable ssl verification for a single git command:
```
git -c http.sslVerify=false
```
then you can use that for pulling, pushing, cloning, etc..
```
git -c http.sslVerify=false push origin master
```
