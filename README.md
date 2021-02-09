[![CircleCI](https://circleci.com/gh/StuKozola/Udacity-CloudDevOps-MachineLearning-Microservices.svg?style=svg)]([<LINK>](https://circleci.com/gh/StuKozola/Udacity-CloudDevOps-MachineLearning-Microservices))

# Udacity-CloudDevOps-MachineLearning-Microservices
Microservice porject for Udacity's nanodegree: Cloud DevOps Engineer

## Project Overview

Goal: Operationalize a Machine Learning app as a Microservice API

Task is to operationalize a pre-trained `sklearn` model that has been trained to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access, teacher-to-pupil ratios, and so on. You can read more about the data, which was initially taken from Kaggle, on [the data source site](https://www.kaggle.com/c/boston-housing). A python flask app—in a provided file, `app.py`—serves out predictions (inference) about housing prices through API calls using the pre-trained model.

### Project Tasks
Goal is to operationalize this working, machine learning microservice using [kubernetes](https://kubernetes.io/), which is an open-source system for automating the management of containerized applications. Task include:
* Test project code using linting (`make lint`)
* Dockerfile to containerize this application (`run_docker.sh`)
* Deploy containerized application using Docker and make a prediction (`upload_docker.sh`) 
* Improve the log statements in the source code for this application (see [app.py](app.py) and[docker_out.txt](output_txt_files/docker_out.txt))
* Configure Kubernetes and create a Kubernetes cluster 
* Deploy a container using Kubernetes and make a prediction (`run_kubernetes.sh`)
* Upload a complete Github repo [repo](https://github.com/StuKozola/Udacity-CloudDevOps-MachineLearning-Microservices) with CircleCI to indicate that code has been tested (badge at top of page)

---

## Files and Directories
```
.circleci/config.yml                        configuration file for CircleCI automated build and testing
app.py                                      flask application for hosting model as a REST api
Dockerfile                                  build instructions for Docker container
Makefile                                    command for setup, installing, and testing project files
make_prediction.sh                          script to test api
model_data/boston_housing_prediction.joblib pre-trained model (sklearn)
model_data/housing.csv                      source data for model        
output_txt_files/docker_out.txt             results of building and running docker container locally
output_txt_files/kubernetes_out.txt         results of local deployment of docker container to kubernetes
README.md                                   You are here
requirements.txt                            python installation dependencies (python 7.3)
run_docker.sh                               script for running the docker container build process
run_kubernetes.sh                           script for running K8s to stand up microservice
upload_docker.sh                            uploads docker container to docker repository
```
---

## Setup the Environment (Linux)

* Run `make setup` to create a virtualenv and activate it `source ~/.devops/bin/activate`
* Run `make install` to install the necessary dependencies
  * Or run `make install all` to set up minkube, docker, and hadolint with python dependencies

### Running `app.py`

1. Standalone:  `python app.py`
2. Run in Docker:  `./run_docker.sh`
3. Run in Kubernetes:  `./run_kubernetes.sh`

### Kubernetes Steps

* Setup and Configure Docker locally (`make install-docker`, `run_docker.sh`, `upload_docker.sh`)
* Setup and Configure Kubernetes locally (`make install-minikube`, `minikube start`)
* Create Flask app in Container (`make lint` to verify docker build and [app.py](app.py))
* Run via kubectl (`run_kubernetes.sh`)
