---
ID: 11083
post_title: My Developer Setup Version 1
author: Dennis
post_date: 2014-11-07 17:13:38
post_excerpt: ""
layout: post
permalink: >
  http://dennisseidel.de/my-developer-setup-version-1/
published: true
slide_template:
  - default
mfn-post-hide-content:
  - "0"
mfn-post-sidebar:
  - "0"
mfn-post-slider:
  - "0"
mfn-post-love:
  - "0"
dsq_thread_id:
  - "3431395339"
---
Since I switch from my architect position designing smart systems to it specialist developing this solution myself. My learning is that I need several environment that I can adapt very flexible. In the following post I will describe what tools I use to create this adaptive Setup.

The foundation of all developer setup is the hardware. I currently use an 11 inch macbook air. But I am no advocate of Apple even though my employer has a close partnership with the green fruit :) There I advice to search a portable devices with a long battery life and enough power to run at least one virtual machine with out performance issues. I actually advice to use a Windows devices because there is better support for Office and Productivity products that you will need in the business life.

The development environment are several virtual machines one for mobile development where I use a hackingtosh as my OS. For my connectivity/internet of things and smart industry development environment I use a set of Unix (centOS) based machine. Most of them I start in headless mode via <a href="https://www.vagrantup.com/">vagrant</a>. This way I can set up a complete DevOps system and mirror the environment of my customers on my machine.

The configuration and installation of all machine includes chef and the scripts for chef (cookbooks) are under source control with git on jazz.net.

I will extend this post with further details and the topics like my editor vim, my terminal configuration with dotfiles and zsh as well as my keybinding management.  To be continued ...