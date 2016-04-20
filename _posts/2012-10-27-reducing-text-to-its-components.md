---
ID: 10974
post_title: 'Reducing text to it&#8217;s components'
author: Dennis
post_date: 2012-10-27 14:03:56
post_excerpt: ""
layout: post
permalink: >
  http://dennisseidel.de/reducing-text-to-its-components/
published: true
image:
  - ""
seo_follow:
  - 'false'
seo_noindex:
  - 'false'
mfn-post-love:
  - "0"
---
This short phyton programm takes a Webpage as an input and reduces it to it's components. The components are the words on the webpage. You can use this and customize this to fit your purpose. This code can be applied in web-crawlers, text analytics and other fields. For example if you want do leave out stop words you would define a dictonary of this word and include this with anouther if statement. This could be applied if you want to reduce patent data to it's components and leave generic terms like 'a' 'this' 'innovation' etc. out. You would do this because words like this have no information value.
<blockquote>
<blockquote>[sourcecode language="python"]

def remove_tags(source):

output = [ ]

atsplit = True

splitlist = [' ','&gt;','&lt;','n']

i = 0

while i &lt; len(source):

if source[i] == '&lt;':

i = source.find('&gt;',i+1)

if source[i] in splitlist:

atsplit = True

else:

if atsplit:

output.append(source[i])

atsplit = False

else:

output[-1] = output[-1] + source[i]

i = i + 1

return output[/sourcecode]

&nbsp;</blockquote>
<p style="text-align: left;"></p>
<p style="text-align: left;">Verwandte Artikel:</p>
</blockquote>
<div class="zemanta-articles">
<ul class="zemanta-articles">
	<li><a href="http://www.information-management.com/infodirect/2011_258/how-to-incorporate-textual-data-into-the-analytics-program-10023064-1.html">Going Beyond the Numbers: How to Incorporate Textual Data into the Analytics Program</a></li>
	<li><a href="http://jugad2.blogspot.com/2012/10/swapping-pipe-components-at-runtime.html">Vasudev Ram: Swapping pipe components at runtime with pipe_controller</a></li>
	<li><a href="http://mikecann.co.uk/personal-project/tinkering-with-typescript/">Tinkering With TypeScript</a></li>
	<li><a href="http://erratasec.blogspot.com/2012/10/a-question-for-cryptomath-peoples.html">A question for crypto/math peoples</a></li>
</ul>
<div class="zemanta-pixie"><img class="zemanta-pixie-img" alt="" src="http://img.zemanta.com/pixy.gif?x-id=6f8ede88-8129-889d-91fb-a057b58ae726" /></div>
</div>