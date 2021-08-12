This project aims to create full CI/CD Pipeline for microservice based applications using [Spring Petclinic Microservices Application](https://github.com/spring-petclinic/spring-petclinic-microservices). Jenkins Server deployed on Elastic Compute Cloud (EC2) Instance is used as CI/CD Server to build pipelines.

# MSP 1 - Prepare Development Server Manually on EC2 Instance

* Prepare development server manually on Amazon Linux 2 for developers, enabled with `Docker`,  `Docker-Compose`,  `Java 11`,  `Git`.
 
 # MSP 2 - Prepare GitHub Repository for the Project

* Connect to your Development Server via `ssh` and clone the petclinic app from the repository p[Spring Petclinic Microservices App](https://github.com/clarusway/petclinic-microservices.git).

## MSP 3 - Check the Maven Build Setup on Dev Branch
* Test the compiled source code.

``` bash
./mvnw clean test 
```
## MSP 4 - Prepare a Script for Packaging the Application
like .mvn clean pacckage
## MSP 5 - Prepare Development Server Cloudformation Template

## MSP 6 - Prepare Dockerfiles for Microservices # ingat balik Docker dgn dockerfile,dockcompose
microsevc architecture; we need bt docker images dulu
utk bt docker images kena bt dgn microsvc(dockerfile
## MSP 7 - Prepare Script for Building Docker Images
put all docker build in one file and execute all in one time
## MSP 8 - Create Docker Compose File for Local Development
 have multi container with diferent svc
 that can be used to bring up an application and the suite of services it depends on with just one command. Compose works in all environments: production, staging, development, testing, as well as CI workflows, although Compose is ideal for development and testing environments.
———The Compose file provides a way to document and configure all of the application’s service dependencies (databases, queues, caches, web service APIs, etc). Using the Compose command line tool you can create and start one or more containers for each dependency with a single command (docker-compose up).

## MSP 10 - Prepare and Implement Selenium Tests 
#silenium final test, unittestdeal dgn line src code, funxtion test ;how the apps works cthnya tls dns name jd wbpg dtg bila dth apa kita mau smua load dan akan buka aapa2 yg kita cllick, bila kita filter smua akan tnjukkn based apa kita mau.tp xposible sbg mnusia utk test smua app. in order automate to  proces test the proces, speed up proces kna bt dgn silenium utk cuba. MCMNA GUNA DENGAN SETIAP BROWSER

## MSP 11 - Prepare Jenkins Server for CI/CD Pipeline
Set up a Jenkins Server and enable it with `Git`,  `Docker`,  `Docker Compose`,  `AWS CLI v2`, `Python`,  `Ansible` and `Boto3`.  To do so, prepare a [Cloudformation template for Jenkins Server](./msp-11-jenkins-server-cfn-template.yml)
## MSP 12 - Configure Jenkins Server for Project

## MSP 13 - Prepare Continuous Integration (CI) Pipeline
We configured a webhook on github and created a Jenkins job so that every time a developer commits code to the specified branches, Jenkins checkouts the code from github (SCM) then builds and tests (unit test) the source code. We build and test the code with Maven script that we created on the same Jenkins job.
We created another pipeline for functional test. We set a cronjob for this pipeline so it runs on every night automatically. When this pipeline starts, it checkouts the source code from SCM, builds and tests (unit tests) with Maven, creates docker images and pushes the images to AWS ECR, creates the infrastructure with Ansible scripts (integrated to Jenkins pipeline), deploy the docker images to the environment and runs functional tests with Selenium and Ansible.

AND WE CAN START DO Create Docker Registry for Dev Manually

## MSP 16 - Create a QA Automation Environment with Docker Swarm
TESTING ON HERE WE CAN USE DYNAMIC INVENTORY FOR ANSIBLE, prepare cfn for docker swarm infrasstructure like we will have 1-2 manager node and few worker node.

## MSP 22 - Prepare Petlinic Kubernetes YAML Files
eeping the deployment files of Petclinic App on Kubernetes cluster, for discovery server adn aother microsvc
Update `vets-service-ingress.yaml` file with following setup to pass the api requests to `vets service` microservice.
Create `kustomization.yml` and `replica-count.yml` files for staging envrionment

Prepare a Staging Pipeline, production

## MSP 28 - Setting Domain Name and TLS for Production Pipeline with Route 53
Create an `A` record of `petclinic.clarusway.us` in your hosted zone (in our case `clarusway.us`) using AWS Route 53 domain registrar and bind it to your `petclinic cluster`.

* Configure TLS(SSL) certificate for `petclinic.clarusway.us` using `cert-manager` on petclinic K8s cluster with the following steps.

* Log into Jenkins Server and configure the `kubectl` to connect to petclinic cluster by getting the `Kubeconfig` file from Rancher and save it as `$HOME/.kube/config` or set `KUBECONFIG` environment variable.

onitoring with Prometheus and Grafana

* Change the port of Prometheus Service to `9090`, so that Grafana can scrape the data.

* Create a Kubernetes `NodePort` Service for Prometheus Server on Rancher to expose it.
   
* Create a Kubernetes `NodePort` Service for Grafana Server on Rancher to expose it