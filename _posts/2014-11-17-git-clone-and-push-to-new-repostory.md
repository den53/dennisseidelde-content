---
ID: 11135
post_title: Git clone and push to new repostory
author: Dennis
post_date: 2014-11-17 16:41:33
post_excerpt: ""
layout: post
permalink: >
  http://dennisseidel.de/git-clone-and-push-to-new-repostory/
published: true
mfn-post-love:
  - "0"
dsq_thread_id:
  - "3431394227"
---
<p>For my mobile application I wanted to start from the ibm sample bluemix application ‘bluelist’ but then store my source code in my own repository at github. For this to do I as follows :  </p>
<ol>
<li>I create a new repo at github. </li>
<li>I clone the repo from the ibm repo to my local machine. </li>
<li>git remote rename origin upstream </li>
<li><span style="color: #333333; font-family: Consolas, 'Liberation Mono', Menlo, Courier, monospace; font-size: 14px;">git remote add origin </span><span class="js-live-clone-url" style="box-sizing: border-box;">git@github.com:den53/bluelist.git</span></li>
<li><span style="color: #333333; font-family: Consolas, 'Liberation Mono', Menlo, Courier, monospace; font-size: 14px;">git push -u origin master</span></li>
</ol>
<p>To pull in patches from upstream, I simply run git pull upstream master &amp;&amp; git push origin master.</p>
<p> </p>