---
ID: 11278
post_title: 'Use Java 8 on Bluemix: How to use a custom buildpack'
author: Dennis
post_date: 2015-05-14 14:55:11
post_excerpt: ""
layout: post
permalink: >
  http://dennisseidel.de/use-java-8-on-bluemix-how-to-use-a-custom-buildpack/
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
  - "3763549830"
---
<p>The default java runtime is the ibm provides liberty profile. Which has very good additional features that increase performance, but is currently (May, 2015) still on Java 7. So when you want to use Java 8 features in your application you just have to deploy a customer build pack which is not more then to a just the <strong><em>manifest.yml</em></strong> file in the root directory of your application. And there you have to change the line with the <em>buildpack:</em> to <strong>https://github.com/cloudfoundry/java-buildpack</strong>. The result should look something like this.</p>

<p><img src="https://c2.staticflickr.com/6/5441/17640540725_a610485dc3_z.jpg" alt="buildpack bluemix java 8 " /></p>