---
ID: 11126
post_title: >
  Developing a hybrid Mobile Application
  on Bluemix
author: Dennis
post_date: 2014-11-17 15:44:49
post_excerpt: ""
layout: post
permalink: >
  http://dennisseidel.de/developing-a-hybrid-mobile-application-on-bluemix-2/
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
  - "3431394394"
---
In this post I will document how to develop an mobile application on the IBM Bluemix Plattform in under 1 hour.
<ol>
	<li>First you have to set up your mobile development environment especially install npm, cordova, ionic, bower and git (on OSX I suggest using hombrew). [code]npm install -g cordova
npm install -g ionic
sudo npm install ios-sim -g
npm install -g bower[/code]</li>
	<li>To understand how hyrids apps with Cordova work you should read up on it (<a href="http://cordova.apache.org/docs/en/3.3.0/guide_platforms_android_index.md.html#Android%20Platform%20Guide">Cordova Getting Started Guide for Android</a> / <a href="http://cordova.apache.org/docs/en/3.3.0/guide_platforms_ios_index.md.html#iOS%20Platform%20Guide">Cordova Getting Started Guide for IOS</a>).</li>
	<li>Clone the app with git to your drive:  [code]git clone https://hub.jazz.net/git/mobilecloud/bluelist-mobiledata[/code]</li>
	<li>Create a boilerplate application on IBM Bluemix</li>
	<li>Configure the Application for use with Bluemix (www/bluelist.json).
[code]{ "applicationId": "INSERT_APPLICATION_ID_HERE", "applicationSecret": "INSERT_APPLICATION_SECRET_HERE", "applicationRoute": "INSERT_APPLICATION_ROUTE_HERE" }[/code]</li>
	<li>Modern mobile web applications are now built using dependency managers. The hybrid application sample uses bower for the client side components. This includes the pulling down of the latest levels of the <a href="https://hub.jazz.net/user/mobilec">Mobile Cloud SDKs</a></li>
	<li style="display: inline; list-style: none;">
<ol>
	<li>From the sample app directory, run [code]bower install[/code]</li>
	<li>To check the development runtime, make sure all existing copies of chrome have been shutdown.</li>
	<li>Load chrome with web security turned off, this enables the mobile testing to avoid any Cross Origin.</li>
	<li style="display: inline; list-style: none;">
<ol>
	<li>On Mac: [code]open -a Google\ Chrome --args --disable-web-security[/code]</li>
	<li>On Windows: [code]start chrome.exe --disable-web-security[/code]</li>
</ol>
</li>
	<li>From the app directory, run <code style="font-size: 12px; font-family: Courier, 'Courier New'; border: 1px solid #dddddd; border-radius: 3px; padding: 0px 5px; box-sizing: border-box; background-color: #fafafa;">ionic serve</code></li>
	<li>The hybrid component should now be visible in chrome browser. The ionic tools support live reload, so if you edit the code you can see if refresh in the browser.</li>
	<li>The sample app can be accessed using this local url: http://localhost:8100/#/tab/list</li>
</ol>
</li>
	<li>You need to make sure you have the latest xcode and android development tools installed on your development environment.
<ol>
	<li>From the sample app directory run the following command to build the sample for iOS: [code]ionic build ios[/code]</li>
	<li>To run it in the emulator you can run emulate command.</li>
	<li>[code]ionc emulate ios[/code]</li>
	<li>You should now see the bluelist-cordova app now running inside the IOS Simulator.</li>
</ol>
</li>
</ol>
<div>

If you want to test with Android make sure you add the android platform to the project.
[code]cordova platform add android[/code]
Do not add the Bluemix Cordova plugin to this project. Dependencies will conflict. If you'd like to use the Cordova Bluemix plugins check out the Dev Works articles for mobile data <a href="http://www.ibm.com/developerworks/mobile/library/mo-bluemix-cordova-plugin/index.html">here</a> and push notifications <a href="http://www.ibm.com/developerworks/mobile/library/mo-cordova-push-app/index.html">here</a>.

</div>