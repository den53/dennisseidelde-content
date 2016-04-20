---
ID: 383
post_title: 'Implemented a ROT13  Encryption Web App'
author: Dennis
post_date: 2012-12-24 23:55:13
post_excerpt: ""
layout: post
permalink: >
  http://dennisseidel.de/implemented-a-rot13-encryption-web-app/
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
  - "3757026753"
---
<pre>The Source Code for the Python Web App using Templates (jinja2):
[sourcecode language="python"]
import os #http://effbot.org/librarybook/os.htm operating system fumctions
import re #http://effbot.org/librarybook/re.htm regular expression module
from string import letters

import webapp2
import jinja2

from google.appengine.ext import db

template_dir = os.path.join(os.path.dirname(__file__), 'templates')
jinja_env = jinja2.Environment(loader = jinja2.FileSystemLoader(template_dir), autoescape = True)

def render_str(template, **params):
    t = jinja_env.get_template(template)
    return t.render(params)

class MainHandler(webapp2.RequestHandler):
    def render(self, template, **kw):
        self.response.out.write(render_str(template, **kw))

    def write(self, *a, **kw):
        self.response.out.write(*a, **kw)

class Rot13(MainHandler):
    def get(self):
        self.render('rot13-form.html')

    def post(self):
        rot13 = ''
        text = self.request.get('text')
        if text:
            rot13 = text.encode('rot13')

        self.render('rot13-form.html', text=rot13)

app = webapp2.WSGIApplication([
        ('/', Rot13)],
                              debug=True)
[/sourcecode]
Source code for the Template positioned in a folder 'templates':
[sourcecode language="html"]&lt;/pre&gt;
&lt;!DOCTYPE html&gt;

&lt;html&gt;
 &lt;head&gt;
 &lt;title&gt;Unit 2 Rot 13&lt;/title&gt;
 &lt;/head&gt;

&lt;body&gt;
 &lt;h2&gt;Enter some text to ROT13:&lt;/h2&gt;
 &lt;form method=&quot;post&quot;&gt;
 &lt;textarea name=&quot;text&quot;
 style=&quot;height: 100px; width: 400px;&quot;&gt;{{text}}&lt;/textarea&gt;
 &lt;br&gt;
 &lt;input type=&quot;submit&quot;&gt;
 &lt;/form&gt;
 &lt;/body&gt;

&lt;/html&gt;[/sourcecode]