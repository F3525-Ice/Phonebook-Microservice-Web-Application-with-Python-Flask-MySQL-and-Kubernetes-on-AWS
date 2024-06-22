# Project: Microservice Architecture for Phonebook Web Application (Python Flask) with MySQL using Kubernetes.

## Description

The Phonebook Microservice Web Application project aims to create a web application with a MySQL database using Docker and Kubernetes. This project helps students understand microservice architecture. The application comprises a frontend service and a backend service to interact with the database service. Each service will be managed by a Kubernetes deployment. The backend service acts as a gateway for the application, serving web pages for create, delete, and update operations, while the frontend service provides a search page for read operations. To ensure data persistence, the project uses persistent volume and persistent volume claim concepts.

## Problem Statement

- Your team is tasked with developing a Phonebook Application as a web service.

- The developers have already designed the initial Phonebook application and database schema, which includes fields for id, name, and number.

- They have implemented a RESTful web service using Python Flask, providing HTTP methods as outlined in the Phonebook API.

- As a cloud engineer, your objective is to deploy this application on an AWS EC2 Instance using Docker and Kubernetes to demonstrate the project's functionality. Key tasks include:

  - Pulling the application code from your team's GitHub repository.

  - Creating Docker images for create/update/delete and search functionalities using Dockerfiles.

  - Deploying the application using Kubernetes, including setting up a MySQL database service and utilizing a custom network for services.

- In the Kubernetes environment, you'll configure three deployments along with their services, and set up a persistent volume for MySQL deployments. Below are the definitions for the required Kubernetes objects:

  1. CREATE/DELETE/UPDATE DEPLOYMENT

  - Configure create/delete/update operations with one or more replicas.

  - Expose container port 80.

  - Set environmental variables for database connection.

  - Protect passwords using Kubernetes secrets.

  - Define the Database Host value in the deployment using Kubernetes ConfigMap.

  2. CREATE/DELETE/UPDATE SERVICE

  - Attach to CREATE/DELETE/UPDATE Deployment.

  - Service type should be NodePort, published on port 30001.

  - Expose port and target port on port 80.

  3. SEARCH DEPLOYMENT

  - Configure search operations with one or more replicas.

  - Expose container port 80.

  - Set environmental variables for database connection.

  - Protect passwords using Kubernetes secrets.

  - Define the Database Host value in the deployment using Kubernetes ConfigMap.

  4. SEARCH SERVICE

  - Attach to SEARCH Deployment.

  - Service type should be NodePort, published on port 30002.

  - Expose port and target port on port 80.

  5. DATABASE DEPLOYMENT

  - Use mysql:5.7 image pulled from Docker Hub.

  - Expose container port 3306.

  - Set environmental variables appropriately.

  - Attach a persistent volume to this deployment.

  - Protect passwords using Kubernetes secrets.

  6. DATABASE SERVICE

  - Attach to DATABASE Deployment.

  - Service type should be ClusterIP.

  - Expose port and target port on port 3306.

  7. Persistent Volume

  - Set volume capacity to 20Gi.

  - Access Mode should be ReadWriteOnce.

  - Host path should be set as /mnt/data.

  - Define a persistent volume claim to attach this volume.

  8. Kubernetes Environment

  - Configure two EC2 instances: one as master and one as worker.

  - Select minimum t2.medium instance type.

  - Ensure the web application is accessible via web browser from anywhere.

  - Use Cloudformation to download application files from GitHub repo and deploy on EC2 Instance using user data script.

## Project Skeleton

```text
Phonebook Microservice Web Application with Python Flask, MySQL, and Kubernetes on AWS (folder)

Initial files:

1. README.md                      # Project definition provided to students
2. Image_for_web_server           # Components for Python Flask Web API (Update/delete/add record)
  - app.py      
  - requirements.txt              
  - templates
    - index.html
    - add-update.html
    - delete.html
3. image_for_result_server        # Components for Python Flask Web API (search record)
  - app.py           
  - requirements.txt              
  - templates
    - index.html

Requested files:

ADD/DELETE/UPDATE DEPLOYMENT AND SERVICE
1. Dockerfile                     # Provided by students 
2. web_server_deployment.yml      # Provided by students
3. web_server_service.yaml        # Provided by students

SEARCH DEPLOYMENT AND SERVICE
1. Dockerfile                     # Provided by students
2. result_server_deployment.yml   # Provided by students
3. result_server_service.yaml     # Provided by students

DATABASE DEPLOYMENT AND SERVICE
1. mysql_deployement.yml          # Provided by students
2. mysql_service.yaml             # Provided by students
3. persistent_volume.yaml         # Provided by students
4. persistent_volume_claim.yaml   # Provided by students

SECRETS AND CONFIGMAP
1. mysql-secret.yaml              # Provided by students
2. database_configmap.yaml        # Provided by students
3. servers_configmap.yaml         # Provided by students
```

## Expected Outcome

### Learning Objective;
Upon completion, students will gain proficiency in:

- Configuring MySQL database.

- Building Docker images.

- Setting up Kubernetes for Python Flask applications.

- Utilizing Kubernetes service objects for networking.

- Configuring AWS EC2 Instances and Security Groups.

- Using Git and GitHub for version control.

- Deploying a web application on AWS EC2 using GitHub as the codebase.

- Building Kubernetes infrastructure with Cloudformation.

## Steps to Solution
  
- Step 1: Download or clone project definition from `F3525-Ice` repo on Github

- Step 2: Create your Kubernetes environment with cloudformation template

- Step 3: Prepare Dockerfiles for search and delete/update/create pages using Python Flask Apps, create images and push to your Docker Hub Repository.

- Step 4: Prepare search, delete/update/create and mysql parts.

- Step 5: Deploy your work on Kubernetes to showcase your application within your team.


## Resources

- [Kubernetes Documentations](https://kubernetes.io/docs/home/)
