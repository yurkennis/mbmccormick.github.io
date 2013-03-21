---
title: Deploying PHP Applications to Heroku
author: Matt
layout: post
permalink: /2012/03/deploying-php-applications-to-heroku/
categories:
  - Development
tags:
  - heroku
  - php
---
# 

I’ve been trying to find a straight-forward guide on how to deploy PHP applications to Heroku to share with people, but I can’t find one that covers both setting up Heroku and deploying PHP applications. While no configuration is necessary to deploy a PHP application on the Cedar stack, I think this guide will be a useful reference.

### Local Workstation Setup

Download the [Heroku Toolbelt][1] for your platform. This will install the [Heroku command line interface][2] for creating and managing Heroku apps, [Foreman][3] for running your applications locally, and Git for pushing to Heroku.

 [1]: https://toolbelt.herokuapp.com/
 [2]: http://devcenter.heroku.com/articles/heroku-command
 [3]: https://github.com/ddollar/foreman

Once you install these tools, open up your command shell and login to your Heroku account.

`$ heroku login`  
`Enter your Heroku credentials.`  
`Email: matt@example.com`  
`Password:`  
`Could not find an existing public key.`  
`Would you like to generate one? [Yn]`  
`Generating new SSH public key.`  
`Uploading ssh public key /Users/matt/.ssh/id_rsa.pub`

You are now ready to create a Heroku application.

### Creating Applications on Heroku

In the working directory for your application, open up your command shell create a new application on the [Cedar stack][4]. Heroku will automatically generate a name for your application, which you can change later, and add the `heroku` remote to your local Git repository.

 [4]: http://devcenter.heroku.com/articles/cedar

`$ heroku create --stack cedar`  
`Creating stark-fog-398... done, stack is cedar`  
`http://stark-fog-398.herokuapp.com/ | git@heroku.com:stark-fog-398.git`  
`Git remote heroku added`

You are now ready to deploy your application to Heroku.

### Deploying to Heroku

Deploying to Heroku is extremely easy. In the working directory for your application, open up your command shell and push to Heroku. Git will display the output from Heroku of the deployment as well as the URL to your application once the deployment has succeeded.

`$ git push heroku master`

You can check the status of your application with `heroku logs` in the event that your deployment failed. Heroku also has several [addons][5] available for databases, cron jobs, background workers, etc. This is a great platform for developing applications with early on and makes it easy to grow and scale your application down the road.

 [5]: https://addons.heroku.com/