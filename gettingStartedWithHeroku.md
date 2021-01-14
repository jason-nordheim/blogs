# Getting Started: Heroku and Node

It doesn't matter how cool your application is, how many features it has, or how useful it is if no one can use it. In order to get people using it, you need to deploy it. [Heroku](https://www.heroku.com) is a development platform designed to help developers get their applications out to their end-users.

> There are a ton of vendors that offer deployment services, including AWS, Google Cloud Platform/Firebase, and many more. Each vendor will vary in both the features offered, as well as pricing and ease-of-use.

# Deployment Checklist

In a dream world, we might have a magic button that deploys our applications in a single step. However, in the real world - there is some pre-work required in order to get the application ready for deployment.

In the case of deploying a Node application to Heroku, that pre-work includes the following:

1. Dynamic Port Binding
2. Specify Node Environment
3. Specify Start Script
4. Create .gitignore

> The steps for competing platforms is very similar
