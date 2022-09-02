This project has passed. CircleCI Status Badge below.

[![CircleCI](https://dl.circleci.com/status-badge/img/gh/oluwatola/project-ml-microservice-kubernetes/tree/main.svg?style=svg)](https://dl.circleci.com/status-badge/redirect/gh/oluwatola/project-ml-microservice-kubernetes/tree/main)

## Project Overview - Completed

In this project, I have applied the skills acquired in this course to operationalize a Machine Learning Microservice API. 

I was given a pre-trained, `sklearn` model that has been trained to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access, teacher-to-pupil ratios, and so on. You can read more about the data, which was initially taken from Kaggle, on [the data source site](https://www.kaggle.com/c/boston-housing). This project tested my ability to operationalize a Python flask app—in a provided file, `app.py`—that serves out predictions (inference) about housing prices through API calls. This project could be extended to any pre-trained machine learning model, such as those for image recognition and data labeling.

### Project Tasks

The project goal is to operationalize this working, machine learning microservice using [kubernetes](https://kubernetes.io/), which is an open-source system for automating the management of containerized applications. In this project you will:
* Test your project code using linting
* Complete a Dockerfile to containerize this application
* Deploy your containerized application using Docker and make a prediction
* Improve the log statements in the source code for this application
* Configure Kubernetes and create a Kubernetes cluster
* Deploy a container using Kubernetes and make a prediction
* Upload a complete Github repo with CircleCI to indicate that your code has been tested

You can find detailed steps on executing the project below:

create environment, use t3 small
ssh-keygen -t rsa

cat /home/directory/

copy ssh key

go to github, ssh and gpg keys. create.

go to cloud9 and do git clone ssh clonelink

cd into proper directory

create venv : python3 -m venv ~/.devops

activate venv: source ~/.devops/bin/activate

make install

docker is pre-installed. docker ps to confirm

install hadolint:
sudo wget -O /bin/hadolint https://github.com/hadolint/hadolint/releases/download/v1.16.3/hadolint-Linux-x86_64 && sudo chmod +x /bin/hadolint

hadolint 

make lint : should return Your code has been rated at 10.00/10

install minikube: curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64

minikube version (to confirm)

download kubectl: curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"

install kubectl: sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl

kubectl to confirm

kubectl version --output yaml

start minikube: minikube start

minikube status

kubectl version --output yaml

ensure you're in .devops environment
complete the docker file as required, and be sure to run make lint.
open run_docker.sh and complete.
execute ./run_docker.sh to build and run docker image

wait for success message.

to make prediction, open up new terminal and execute: ./make_prediction.sh

add log statement to app.py by including: LOG.info(f"output prediction: {prediction}").

execute ./run_docker.sh again in another terminal and copy the output to a docker_out.txt file (or execute ./rundocker.sh >> docker_out.txt)

Complete Upload_docker.sh file
set dockerpath="lordthor/microproject:v1.0.0"
authenticate and push docker image.

upload  docker by executing ./upload_docker.sh

run minikube start to run cluster locally.
kubectl config get-contexts
kubectl config view
curl https://192.168.49.2:8443 to check minikube server connectivity

run  ./run_kubernetes.sh to deploy application
run    kubectl get pods    till you see success message for pod creation

call ./run_kubernetes again
in separate terminal, call ./make_prediction.sh

copy output into kubernetes_out.txt

when done testing, stop cluster by executing: minikube stop
use   minikube delete   to clean up resources.

push to github repo and confirm circleci integration (create config.yml file in appropriate directory).

To add circle CI status badge, copy markdown from notifications section of project settings > status badges as shown below:

[![CircleCI](https://dl.circleci.com/status-badge/img/gh/oluwatola/project-ml-microservice-kubernetes/tree/main.svg?style=svg)](https://dl.circleci.com/status-badge/redirect/gh/oluwatola/project-ml-microservice-kubernetes/tree/main)

paste in README.md file.

**The final implementation of the project will showcase your abilities to operationalize production microservices.**

---

Summary of steps:
## Setup the Environment

* Create a virtualenv with Python 3.7 and activate it. Refer to this link for help on specifying the Python version in the virtualenv. 
```bash
python3 -m pip install --user virtualenv
# You should have Python 3.7 available in your host. 
# Check the Python path using `which python3`
# Use a command similar to this one:
python3 -m virtualenv --python=<path-to-Python3.7> .devops
source .devops/bin/activate
```
* Run `make install` to install the necessary dependencies

### Running `app.py`

1. Standalone:  `python app.py`
2. Run in Docker:  `./run_docker.sh`
3. Run in Kubernetes:  `./run_kubernetes.sh`

### Kubernetes Steps

* Setup and Configure Docker locally
* Setup and Configure Kubernetes locally
* Create Flask app in Container
* Run via kubectl