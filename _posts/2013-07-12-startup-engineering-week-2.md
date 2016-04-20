---
ID: 911
post_title: 'Startup Engineering &#8211; setting up a web development environment'
author: Dennis
post_date: 2013-07-12 13:17:53
post_excerpt: ""
layout: post
permalink: >
  http://dennisseidel.de/startup-engineering-week-2/
published: true
image:
  - ""
mfn-post-love:
  - "0"
dsq_thread_id:
  - "3539208782"
---
In the second week they give a introduction in developing web apps in the cloud. They us a combination of Amazon Web Services (aws), Heroku and Github. Basiclly the use a virtual machine on the amazon cloud to develop, store the work on github and push it to heroku to distribute the work via the internet.

<img alt="" src="http://imageshack.us/a/img811/5998/ei3m.png" />

For preperation install <a href="http://www.google.de/intl/de/chrome/browser/">Google Chrome</a> and and the<a href="https://chrome.google.com/webstore/detail/user-agent-switcher-for-c/djflhoibgkdhkhhcedjiklpkjnoahfmg?hl=en-US"> User Agent Switcher</a> (to simulate mobile devices).  Then to use a terminal enviroment you should <a href="http://cygwin.com/">Cygwin</a> (important to ssh into aws you have to install the ssh package) . Then you should sign up for aws, github, gravatar and heruku. I will not cover this, but you can find detailed instruction within the o<a href="http://de.slideshare.net/DennisSeidel/lecture2-interactivestart">fficial course documents</a>.

After the setup lets connect to AWS via Ciygwin:

[sourcecode language="shell"]#Download the ssh.key (e.g. dennisseidel-cs184.pem)
#change to home directory
cd ~
#copy key into ssh directory
cp /cygdrive/c/Users/dennis/Downloads/dennisseidel-cs184.pem .ssh/
#//give file correct permissons
chgrp Users dennisseidel-cs184. &amp;amp;amp;&amp;amp;amp; chmod 400 denniseidel-cs184.pm
#ssh into aws
ssh -i  dennisseidel-cs184.pem ubuntu@ec2-50-19-140-229.compute-1.amazonaws.com
[/sourcecode]

Install heroku and on your AWS Ubuntu:

[sourcecode language="shell"]
# Execute these commands on your EC2 instance.
# Note that -qO- is not -q0-. O is the English letter, 0 is the number zero.
# 1) Install heroku and git
$ sudo apt-get install -y git-core
$ wget -qO- https://toolbelt.heroku.com/install-ubuntu.sh | sh
$ which git
$ which heroku
# 2) Login and set up your SSH keys (
$ heroku login
$ ssh-keygen -t rsa //alternatively if you allready created a ssh-key add it directly
$ heroku keys:add
# 3) Clone a sample repo and push to heroku
$ git clone https://github.com/heroku/node-js-sample.git
$ cd node-js-sample
$ heroku create
$ git push heroku master[/sourcecode]