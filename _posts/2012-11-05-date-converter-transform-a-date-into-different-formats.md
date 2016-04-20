---
ID: 136
post_title: 'Date Converter: Transform a date into different formats'
author: Dennis
post_date: 2012-11-05 15:31:00
post_excerpt: ""
layout: post
permalink: >
  http://dennisseidel.de/date-converter-transform-a-date-into-different-formats/
published: true
image:
  - ""
seo_follow:
  - 'false'
seo_noindex:
  - 'false'
mfn-post-love:
  - "0"
dsq_thread_id:
  - "3718312141"
---
<div>One very common data transformation is the stadardization of dates. This Date Converter Code can be customized to your need. You can use foreign languages or change the order of day, month and year. Also you could include other standardizations like '01' and '1'.</div>
<blockquote>
<div>
<div>[sourcecode language="python"]# Date Converter
# Write a procedure date_converter which takes two inputs. The first is
# a dictionary and the second a string. The string is a valid date in
# the format month/day/year. The procedure should return
# the date written in the form &lt;day&gt; &lt;name of month&gt; &lt;year&gt;.
# For example , if the
# dictionary is in English,
english = {1:&quot;January&quot;, 2:&quot;February&quot;, 3:&quot;March&quot;, 4:&quot;April&quot;, 5:&quot;May&quot;,
6:&quot;June&quot;, 7:&quot;July&quot;, 8:&quot;August&quot;, 9:&quot;September&quot;,10:&quot;October&quot;,
11:&quot;November&quot;, 12:&quot;December&quot;}
# then  &quot;5/11/2012&quot; should be converted to &quot;11 May 2012&quot;.
# If the dictionary is in Swedish
swedish = {1:&quot;januari&quot;, 2:&quot;februari&quot;, 3:&quot;mars&quot;, 4:&quot;april&quot;, 5:&quot;maj&quot;,
6:&quot;juni&quot;, 7:&quot;juli&quot;, 8:&quot;augusti&quot;, 9:&quot;september&quot;,10:&quot;oktober&quot;,
11:&quot;november&quot;, 12:&quot;december&quot;}
# then &quot;5/11/2012&quot; should be converted to &quot;11 maj 2012&quot;.
# Hint: int('12') converts the string '12' to the integer 12.
def date_converter(dic, string):
first_split = string.find('/')
month = string[0:first_split]
second_split = string.find('/',first_split+1)
day = string[first_split+1:second_split]
year = string [second_split+1:]

month_name= dic[int(month)]

return day+' '+month_name+' '+year
print date_converter(english, '5/11/2012')
#&gt;&gt;&gt; 11 May 2012
print date_converter(english, '5/11/12')
#&gt;&gt;&gt; 11 May 12
print date_converter(swedish, '5/11/2012')
#&gt;&gt;&gt; 11 maj 2012
print date_converter(swedish, '12/5/1791')
#&gt;&gt;&gt; 5 december 1791[/sourcecode]

</div>
</div></blockquote>
<div class="zemanta-articles">Verwandte Artikel:
<ul class="zemanta-articles">
	<li><a href="http://www.daniweb.com/software-development/cpp/threads/437747/how-do-i-combine-2-c-style-strings-into-an-if-statement">How do I combine 2 C-Style Strings into an if statement</a></li>
	<li><a href="http://www.daniweb.com/software-development/threads/437739/how-do-i-combine-two-c-style-strings-together">How do I combine two c-style strings together?</a></li>
	<li><a href="http://stackoverflow.com/questions/12919067/convert-date-string-est-to-java-date-utc">Convert date string (EST) to Java Date (UTC)</a></li>
	<li><a href="http://www.daniweb.com/software-development/java/threads/435292/concatenating-strings-in-java-symbols-cant-be-recognized">Concatenating Strings in Java (symbols can't be recognized)</a></li>
</ul>
<div class="zemanta-pixie"><img class="zemanta-pixie-img" alt="" src="http://img.zemanta.com/pixy.gif?x-id=059225dd-8908-8c10-b8b5-e3eb767faad6" /></div>
</div>