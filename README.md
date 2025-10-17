<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Deploy an App Across Accounts

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-compute-ecr)

**Author:** Nufan Noushad Mohamed  
**Email:** nufannoushad@gmail.com

---

![Image](http://learn.nextwork.org/daring_lavender_zesty_iara/uploads/aws-compute-ecr_3e91948719)

---

## Introducing Today's Project!

In this project, I will be deploying an app acrosss two accounts with a friend. I am Player A and I will be moving my app from one account to another AWS account.

### What is Amazon ECR?

Amazon ECR (Elastic Container Registry) is a fully managed container image registry provided by AWS. It allows you to store, manage, and deploy Docker container images in a secure and scalable way.

### One thing I didn't expect...

One thing I didn't expect in this project was the fact that it was quite spicy and we had to do a lot of debugging together especially on the terminal.

### This project took me...

This project took me. 2 hours My biggest learning was ECR

---

## Creating a Docker Image

I set up a HTML file with some code and a Dockerfile. Both files are needed because Player A needs to be able to see the HTML file and the Dockerfile will allow us to create a container.

My Dockerfile tells Docker to starti with a pre-built container image called Nginx. It's kind of like we’re reusing a recipe (the Nginx image) and adding our own modifications (the rest of my Dockerfile) to customise it for our needs, instead of writing an entirely original recipe from scratch. The 2nd line "COPY index.html /usr/share/nginx/html/" allows us to utilise our written HTML file and serve it on Nginx.

### I also set up an ECR repository

ECR stands for Amazon Elastic Container Registry. It is important because it allows us to have a place to store our container images.

![Image](http://learn.nextwork.org/daring_lavender_zesty_iara/uploads/aws-compute-ecr_e7f8g9h0)

---

## Set Up AWS CLI Access

### AWS CLI can let me run ECR commands

AWS CLI is essentially the way of managing the AWS Console through your command line. The CLI asked for my credentials because it does not currently know me and needs to authenticate this.

To enable CLI access, I set up a new IAM user with the permission Attached Policy. I also set up an access key for this user, which means it will have full access to ECR.

To pass my credentials to the AWS CLI, I ran the command "aws configure" I had to provide both access and secret key.

![Image](http://learn.nextwork.org/daring_lavender_zesty_iara/uploads/aws-compute-ecr_4aa3e4fe6)

---

## Pushing My Image to ECR

Amazon Elastic Container Registry (ECR), push commands are the steps you use to upload (or push) your Docker container image from your local machine to an ECR repository.

### There are three main push commands

To authenticate Docker with my ECR repo, I used the command aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 221045608417.dkr.ecr.us-east-1.amazonaws.com

To push my container image, I ran the command docker. Pushing means to push your container image to ECR

When I built my image, I tagged it with the label latest This means latest is a commonly used tag to represent the most recent version. This way, if you make updates to your code, you can rebuild the image, tag it as latest, and any deployments that reference latest will always pull the most up-to-date version.

---

## Resolving Permission Issues

When I tried pulling my project buddy's container image for the first time, I saw the error "Error response from Daemon" This was because repositories are private by default.

To resolve each other's permission issues we added a JSON policy to the permissions.

![Image](http://learn.nextwork.org/daring_lavender_zesty_iara/uploads/aws-compute-ecr_74b90da414)

---

## Deploying the App

---

## Resolving Deployment Issues

---

---
