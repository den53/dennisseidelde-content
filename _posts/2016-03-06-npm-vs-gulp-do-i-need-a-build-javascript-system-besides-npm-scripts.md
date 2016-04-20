---
ID: 11481
post_title: 'NPM vs Gulp &#8211; Do I need a build javascript system besides npm scripts'
author: Dennis
post_date: 2016-03-06 08:38:03
post_excerpt: ""
layout: post
permalink: >
  http://dennisseidel.de/npm-vs-gulp-do-i-need-a-build-javascript-system-besides-npm-scripts/
published: true
mfn-post-love:
  - "0"
slide_template:
  - default
mfn-post-hide-content:
  - "0"
mfn-post-sidebar:
  - "0"
mfn-post-slider:
  - "0"
dsq_thread_id:
  - "4638380134"
---
#NPM vs Gulp - Do I need a build javascript system besides npm scripts

First when I look at npm vs gulp I was like, well I can do this with npm scripts, why to learn another tool.
So I tried to make it happen with just npm scripts, this worked great until I tried to automatically create
responsive images with imagemagick. This would have required me to write a complete bash script.

*Advantage npm script:*
- I just write my build steps as shell commands and I am independent of the lifecycle of certain tools like gulp. As the bash script is portable.
- I minimize the tooling I need to learn. No need to install an additional command-line tool to run your build.
- They don't have the complexity of a full build tool.

*Advantage gulp:*
- A tool like Gulp gives you the full power of Node and JavaScript.
- They provide consistent APIs optimized for composing build tasks.
- They offer huge ecosystems of plugins for almost anything you can imagine.
- They avoid cross-platform compatibility problems.
- Gulp is javascript and no additional DSL.
- Gulp increases the performance by doing the build steps in parallel.

So I see that gulp is not so much more to learn as I don't have to learn a tool with it's own language. So my decision is I use the best tool for the job if it is in java or javascript.

My solution:

1. I learn gulp and write my build tasks in javascript.
2. I include gulp in my npm scripts with the following code into my 'package.json':

```javascript
{
  &quot;scripts&quot;: {
    &quot;build:prod&quot;: &quot;gulp build --prod&quot;,
    &quot;build:dev&quot;: &quot;gulp build&quot;
  }
}
```