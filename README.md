# DevOps Microservices

[![CircleCI](https://circleci.com/gh/walidoc/DevOps_Microservices.svg?style=svg)](https://circleci.com/gh/walidoc/DevOps_Microservices)

## Cloud9 was used for building the project.

## Project Overview
In this project, operationalize a Machine Learning Microservice API by operationalizing a Python flask app—in a provided file, app.py—that serves out predictions about housing prices through API calls.

## Setup the Environment
  Create a virtualenv and activate it
  Run make install to install the necessary dependencies
  Run make lint to run lint checks on the project code

## Run in Docker: 
  ./run_docker.sh

## Upload docker image to dockerhub
  ./upload_docker.sh

## Installing Kubernetes package, Minikube

## Run in Kubernetes: 
  ./run_kubernetes.sh
  
## Make Predection with ./make_prediction.sh shell script for sending some input data to your containerized application via the appropriate port.
Each numerical value in here represents some feature that is important for determining the price of a house in Boston.