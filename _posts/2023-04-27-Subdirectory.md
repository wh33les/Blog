---
layout: post
title: Subdirectory. 
---
I am trying to change the url of my blog to wh33les.github.io/blog but I can't figure it out.  I followed the directions for Solution 2 on [this page](https://github.com/jbranchaud/blog/blob/master/_posts/2013-03-02-Running-Your-Jekyll-Blog-from-a-Subdirectory.md) but it didn't work.  I also edited the \_config.yml file by changing the url to https://wh33les.github.io/blog and baseurl to "/blog".  I also noticed in that file I have mathjax set to true, so I don't know why I've also had problems rendering LaTeX in my blog posts.  

Now I just reloaded wh33les.github.io and all the formatting went away!  I read Solution 1, but it said to tell the deployment scheme to deploy the blog directory and I don't know how to do that.  But I don't understand why Solution 2 doesn't work.  OK, now I changed everything back and it loads correctly.  I think I had to change permalink back to :title.html.  OK, now I changed permalink to /blog/:title.html and nothing happened, but then when I changed it back /blog shows up in the url of my blog posts now.  But the homepage for the blog is still not under /blog.  I just changed url to https://wh33les.github.io/blog, I noticed there was no s in the name.  Doesn't work.  I tried going to https://wh33les.github.io/blog and just got the blank index.html file I made.
