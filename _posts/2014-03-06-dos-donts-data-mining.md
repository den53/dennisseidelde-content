---
ID: 1269
post_title: The Do’s and Don’ts of Data Mining
author: Dennis
post_date: 2014-03-06 01:23:56
post_excerpt: ""
layout: post
permalink: >
  http://dennisseidel.de/dos-donts-data-mining/
published: true
image:
  - ""
mfn-post-love:
  - "0"
slide_template:
  - ""
dsq_thread_id:
  - "3966285718"
---
<ol>
	<li><strong style="line-height: 1.5em;">Do plan for data to be messy. </strong><span>While data is available for mining projects in ever-increasing amounts, it is the rare occasion when it will arrive in a tidy, mining-ready format. More typically, it will show up in multiple spreadsheets that vary in format and granularity. These varied formats frequently require hours (and hours) of ETL (Extract, Transform, Load) time.</span></li>
	<li><strong style="line-height: 1.5em;">Do create a clearly-defined, measurable objective for every project.</strong><span> While most objectives are good at stating what you want to achieve, it's not the "what" that matters. How will you determine project success? And by when? These three elements...the what, the how, and the when... are not options, they are requirements for a clearly-defined project objective.</span></li>
	<li><strong style="line-height: 1.5em;">Do ask questions. </strong><span>Understanding the problem and asking the right question is more important than using an advanced algorithm.</span></li>
	<li><strong style="line-height: 1.5em;">Do simplify the solution to increase your chances of success</strong><span>. Most Data Scientists are aware that simpler solutions are generally better solutions. Why? Because they have fewer moving parts that can break and there's less likelihood of model overfitting. When simplifying, consider the predictors, but also the target variable... ask, "Can it be simplified as well?"</span></li>
	<li><strong style="line-height: 1.5em;">Do cross-check data coming out of the ETL process with the original values, and with project stakeholders.</strong><span> This is the time to uncover errors in the ETL process or in the raw data, itself. Stakeholder data reviews are critical for making sure everyone agrees that the proper data is being used.  Waiting to uncover anomalies and errors during mining/modeling is too late and wastes everyone’s time. Plots and descriptive statistics can be helpful in spotting issues.</span></li>
	<li><strong style="line-height: 1.5em;">Do use more than one technique/algorithm.</strong><span> Given the availability of tools like SPM and others, “it takes too much time to try multiple techniques” is no longer a valid response. For example, if the problem is one of classification, don’t just use CART and say “that’s the answer.” Random Forests may deliver better results.</span></li>
	<li><strong style="line-height: 1.5em;">Do be informed.</strong><span> Stay fluent on the latest data mining concepts and approaches, as well as data mining history.</span></li>
</ol>
<h3 align="center">The Don'ts of Data Mining</h3>
<ol>
	<li><strong>Do Not Ever … I mean EVER underestimate the power of good data preparation. </strong>THE number one mistake that Modelers make is related to lousy or totally absent data preparation prior to model development. Good data prep includes cleaning, transforming, and aggregating model input data as well as the identification and treatment of outliers.</li>
	<li><strong>Don’t use the default model accuracy metric. </strong>The default metric for continuous valued prediction is R-squared or the average squared error or mean squared error (MSE). The default metric for classification problems is percent correct classification (PCC). These are both batch metrics that summarize the accuracy of your models in a single number. While some business problems should assess model accuracy using MSE or PCC, these are rare in my experience. Most often, some errors are worse than others and we select models that do more than have good accuracy <em>on average</em>. They are the best at selecting subsets of the population for treatment.</li>
	<li><strong>Don't forget to document all modeling steps and underlying data!</strong></li>
	<li><strong>Don't overfit</strong>...with Big Data it is easy to find patterns even in random data. Use appropriate tests such as randomization tests to avoid finding false patterns in test data, which will not hold later on.</li>
	<li><strong>Do not just collect a pile of data and “toss it into the big data mining engine” to see what comes out.</strong> Domain knowledge is an important cross-check on the variables being used. Extraneous data can reduce model accuracy.</li>
	<li><strong>Do not ascribe them mystical powers and wrongly think “it’s all about the algorithms”.</strong> Don't overly-focus on software, make unfair assumptions about innate algorithmic capabilities, or even the cool software buttons that can be pushed. All are ill-equipped and are poor substitutes for your intelligence, insight, skills, and creative abilities.</li>
	<li><strong>Do not underestimate the power of a simpler-to-understand solution that is slightly less accurate. </strong>A model a client cannot grasp is one that will not be trusted as much as one that “makes sense.”</li>
	<li><strong>Do not Blindly trust assumptions made to satisfy frequency statistics, as well as p-values and AIC.</strong></li>
</ol>
Sources: <a href="http://www.kdnuggets.com/2014/03/data-mining-do-and-dont.html">www.kdnuggets.com</a>