---
layout: post
title: Personal website.
---
This weekend I decided to make a personal website.  Whenever I have a professional website, if I switch jobs then I lose the site.  I wanted to have a permanent place with all of my materials.  I used GitHub Pages to host the site.  [Here](https://wh33les.github.io) is the url.

As I was making the website I spent a lot of time trying to beautify my code as I went along.  I made notes and this post is just going to be a list of issues that arose.

- Each page has a menu bar that includes a link to the homepage, except for the homepage.  For the non-homepages I used JavaScript to call the HTML I used for the header of each page (title, menu) but since the homepage header was different (it doesn't include the Home link) I had to rewrite most of the code in the index.html file.  I feel like there should be a way to use the standardized code and just modify it not to include the Home link on the homepage, but I couldn't find a way.

- My computer is set to use the English International keyboard so I have access to characters with accents.  However, these characters do not work with HTML (or LaTeX, I found out).  I learned the special character code for &eacute; is \&eacute; or \&#233; and the code for &ouml; is 
