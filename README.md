# DevOps Microservices

[![CircleCI](https://circleci.com/gh/walidoc/DevOps_Microservices.svg?style=svg)](https://circleci.com/gh/walidoc/DevOps_Microservices)

## Project Overview
This project is operationalizing a Machine Learning Microservice API. First, docker image is built for the application (app.py file) using docker. This docker image is then uploaded to DockerHub. From DocekrHub, this image can be utilized by Kubernetes to deploy it to the cluster. The application is deployed in kubernetes pod and exposed to the outside world using port forwarding mechanism. The application file app.py serves predictions about housing prices through API calls.

## Setup the Environment
- Create AWS cloud9 environment and clone the project.
- Create a virtual environment and activate it. 
```
  python3 -m venv ~/.devops
  source ~/.devops/bin/activate
```
- Start minikube 
```
  minikube start
```
## Run the project
- Install the project's dependencies found in requirements.txt
```
  make install
```
- Lint the project with pylint and hadolint
```
  make lint
```
### Run in Docker
```
  ./run_docker.sh
```
### Upload docker image to dockerhub
```
  ./upload_docker.sh
```
### Run in Kubernetes: 
```
  ./run_kubernetes.sh
```  
## Files in this project
- requirements.txt: lists python dependencies for the project.
- Makefile: used to run make install, make lint etc.
- run_docker.sh: creates docker image. The image name will be the tag name in the docker file i.e. mlapp
	- Dockerfile will copy app.py, install all dependencies listed in requirements.txt file and expose port 80 where the app is running.
	- The script will build mlapp image. Built images can be checked using "docker images" command.
	- "docker run -p 8000:80" will expose the app at port 8000
- upload_docker.sh: uploads docker image to DockerHub
	- Authenticates DockerHub credentials and pushes the image using docker push command.
- run_kubernetes.sh: runs the image in Kubernetes cluster.
- Run ./make_prediction.sh to send input data to docker image in kubernetes pod and receive house pricing predictions.
- .circleci/config.yml - to automate make install and make lint using continuous integration with github.
