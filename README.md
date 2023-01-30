# Deploying a Flask API

This is my submission for the fourth course in the [Udacity Full Stack Nanodegree](https://www.udacity.com/course/full-stack-web-developer-nanodegree--nd004): Server Deployment, Containerization, and Testing.

In this project I ccontainerised and deployed a Flask API to a Kubernetes cluster using Docker, AWS EKS, CodePipeline, and CodeBuild.

The Flask app that I used consists of a simple API with three endpoints:

- `GET '/'`: This is a simple health check, which returns the response 'Healthy'. 
- `POST '/auth'`: This takes a email and password as json arguments and returns a JWT based on a custom secret.
- `GET '/contents'`: This requires a valid JWT, and returns the un-encrpyted contents of that token. 

The app relies on a secret set as the environment variable `JWT_SECRET` to produce a JWT. As the built-in Flask server is adequate for local development, but not production, I used the production-ready [Gunicorn](https://gunicorn.org/) server when deploying the app.


## Dependencies

- Docker Engine
    - [Docker](https://docs.docker.com/install/).

 - AWS Account
     - [AWS](https://aws.amazon.com/#).
     
## Project Steps

I accomplished this with the following steps:

1. Wrote a Dockerfile for a simple Flask API
2. Built and tested the container locally
3. Created an EKS cluster
4. Stored a secret using AWS Parameter Store
5. Created a CodePipeline pipeline triggered by GitHub checkins
6. Created a CodeBuild stage which builds, tests, and deploys the code


## Useful References/Extra Reading

https://docs.github.com/en/github/using-git/ignoring-files
https://www.atlassian.com/git/tutorials/saving-changes/gitignore
https://help.github.com/en/github/administering-a-repository/setting-repository-visibility
https://www.docker.com/
https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04
https://www.techrepublic.com/article/how-to-use-docker-env-file/
https://www.digitalocean.com/community/tutorials/how-to-read-and-set-environmental-and-shell-variables-on-a-linux-vps
https://stackoverflow.com/questions/21981796/cannot-ping-aws-ec2-instance
https://en.wikipedia.org/wiki/Internet_Control_Message_Protocol
https://en.wikipedia.org/wiki/Uptime
https://en.wikipedia.org/wiki/System_monitor
https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-access-logs.html
https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-troubleshooting.html
http://linuxcommand.org/tlcl.php
https://docs.pytest.org/en/latest/getting-started.html
http://linuxcommand.org/tlcl.php
