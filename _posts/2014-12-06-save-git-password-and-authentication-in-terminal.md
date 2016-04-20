---
ID: 11148
post_title: >
  Save git password and authentication in
  terminal
author: Dennis
post_date: 2014-12-06 00:29:05
post_excerpt: ""
layout: post
permalink: >
  http://dennisseidel.de/save-git-password-and-authentication-in-terminal/
published: true
mfn-post-love:
  - "0"
dsq_thread_id:
  - "3431393861"
---
I was very annoyed with jazz.net as I had to type in my username and password every time I pushed or pulled something to the repository. But then on <a href="http://stackoverflow.com/questions/5343068/is-there-a-way-to-skip-password-typing-when-using-https-github">stackoverflow</a> I found the solution for mac: 

[code]git config --global credential.helper osxkeychain[/code]

this allows you to use the normal OS X keychain to store the git credentials. In the link you find also windows and linux solutions.