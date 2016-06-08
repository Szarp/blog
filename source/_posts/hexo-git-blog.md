---
title: Easy hexo blog
tags:
 - hexo
Categories:
comments: true
date: 2016-06-08
---
Easy hexo blog
### Writing blog "on" github 
If you are hosting your domain, after writing new post you have to upload it. But if it is a blog and everything you publish is public, you can just create a blog repo where you will upload your posts. After that using ```git pull``` on server you will copy all hanges. It makes server administration very easy.
How I have made it.
Install hexo
1. hexo init
3. delete all _git files (like .gitatribute and .git)_
3. create repo with same name
4. move from init folder to repo

Now after some changes you have to just use `git pull` on your server (even without restarting it and you will see them)
