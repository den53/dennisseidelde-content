---
ID: 1126
post_title: 'Soccer Analytics &#8211; Predicting the value of a forwarder the critical goal score'
author: Dennis
post_date: 2013-10-11 12:38:29
post_excerpt: ""
layout: post
permalink: >
  http://dennisseidel.de/soccer-analytics-predicting-value-forwarder-critical-goal-score/
published: true
image:
  - ""
mfn-post-love:
  - "0"
dsq_thread_id:
  - "3586294022"
---
In the world of soccer forwards are the players that generate the highest transfer fees. Especially forwards that score a large amount of goals. But lets remember the season 2012/2013 when Lionel Messi broke the scoring record from Gerd Müller and the FC Bayern Munich had no player scoring more than 20 goals. But still Munich broke every record there were and won every title as well as beating Lionel Messi's FC Barcelona 7:0 in two games.
So total goals is a very bad benchmark for the value of a forwarder. Still the job of an forwarder is to score thats why I develop the critical goal score, taking into account importance and difficulty.

<strong>Importance:</strong> To identify the important game deciding goals I identify all goals that are needed for the team to win or tie. The intuition behind this is that goal 2 to 6 in a 6:0 are much less important than goal 1 to 2 in an in an 2:1.  We then identify point contributed by multiplying the resulting gain in point {1,3} by the amount of critical goals this player scored divided by the number of all critical goals needed to gain the points.

<strong> Difficulty: </strong>The other dimension is how difficult it is to score a goal against the opponent. A goal that resulted in winning against FC Bayern Munich should could more than the goals that help you win against Werder Bremen. Because the defence of FC Bayern is much harder to play out than the defence of Werder Bremen. As were using data from the past we can simple use the goals scored against this team divided by sum of all goals scored against every team at the of the year.

This value is better than the overall goals scored but still this is looking into the past. To predict the future value of a player you should use the development in this score and the correlation to other "internal values" fitness test scores, weight, speed and psychological profiles. Then you can can live predict how the development of this score continuous. This is necessary because the past is not a good indicator for the future!

Finally this number can be used to identify the real value of buying a player. Therefore you multiply the value the average point gained by this player with the money this points will generate in revenue from the league and tv plus his merchandising/marketing value. Then we use the NPV and Real Option Approach for valuing the opportunity to buy a player out of his contract.