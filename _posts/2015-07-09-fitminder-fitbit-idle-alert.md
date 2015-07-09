---
layout: post
title: Fitminder - Fitbit Idle Alert
date: 2015-07-09 00:00
comments: true
categories: []
---
I love my <a href="http://fitbit.com">Fitbit</a>. I consider myself to be quite the <a href="http://quantifiedself.com">quantified self</a> nerd. Though one thing I wish my Fitbit had is an idle alert. <a href="http://jawbone.com">Jawbone</a>'s <a href="https://jawbone.com/up">UP wearables</a> do a great job at this. When your fitness tracker detects that you've been sitting idle for too long, it will give you subtle nudge to get moving by vibrating. It's not clear whether this is on Fitbit's roadmap, but that didn't stop me from creating my own implementation for it. Enter <a href="http://fitminder.herokuapp.com">Fitminder</a>.

Fitminder is s simple web service that monitors your Fitbit activity and will send you a text message when you haven't moved in a while. The application itself is a <a href="http://nodejs.org">node.js</a> + <a href="http://expressjs.com">Express</a> website running on <a href="http://heroku.com">Heroku</a>. I use <a href="http://twilio.com">Twilio</a> as my telephony provider and <a href="http://stripe.com">Stripe</a> as my payments provider. When you sign up for Fitminder, the application creates a <a href="http://wiki.fitbit.com/display/API/Fitbit+Subscriptions+API">subscription</a> with the <a href=http://dev.fitbit.com>Fitbit API</a> against your Fitbit account. Then anytime you sync your Fitbit, Fitminder receives a notification that your data has changed and then makes a follow up request to fetch that data. It analyzes your activity history and determines whether or not you've been sitting idle for too long. If you have, it sends you a friendly reminder in the form of a text message.

I originally started the project for myself, but after <a href="http://www.reddit.com/r/fitbit/comments/31jecl/fitminder_an_idle_alert_for_your_fitbit/">sharing it</a> to <a href="http://reddit.com">Reddit</a>, it quickly took off. The number of users quickly grew and, along with it, so did my <a href="http://en.wikipedia.org/wiki/Cost_of_goods_sold">COGS</a>. So I had to implement a small payment model to help cover the costs of sending text messages and scaling out. All in all, the results have been pretty surprising. My last analysis showed that the average Fitbit user walked an average of 2,500 more steps per day in the 30 days after signing up for Fitminder than they did in the 30 days before they signed up. 

You can check out the <a href="http://github.com/mbmccormick/fitminder">source code</a> on GitHub or signup at <a href="http://fitminder.herokuapp.com">http://fitminder.herokuapp.com</a>.