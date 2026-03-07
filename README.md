# CI/CD Pipeline for containerized Web App on AWS with Terraform & GitHub Actions

## Project Overview

This project demonstrates an automated CI/CD workflow that provisions and deploys a containerized web application using Terraform, GitHub Actions, Docker, and AWS EC2.

The application is based on the Docker Samples visit counter example. It consists of a **Node.js application** behind an **Nginx reverse proxy**, with a **Redis database** used to store the visit count. The setup includes two servers behind a load balancer, every time the app is accessed it will display the total number of visits and which server handled the request. The point is to illustrate the load balancing behavior in a distributed environment.

Infrastructure is defined using **Terraform**. It provisions an AWS EC2 instance running the latest Ubuntu image, installs Docker and Docker Compose, clones this repository, and builds the application containers.

Deployment is orchestrated through a **GitHub Actions pipeline**. Every push to the main branch triggers the workflow, which:
- Applies the Terraform configuration to create the infrastructure
- Builds and runs the containerized application on the instance
- Keeps the environment running for 5 nutes
- Destroys all provisioned resources to avoid unnecessary cloud costs


## Run app locally

1. Clone this repository and cd to it

2. Start Docker locally with `$ docker compose up --build`

3. Access `http://localhost:80` on the browser or run `$ curl localhost:80`

4. Tear it down with `$ docker compose down`



## Deploy app

1. Fork this repository

2. Create repository secrets for your AWS Access Key

3. Push a commit to trigger the pipeline

4. Access app through public IP displayed on logs