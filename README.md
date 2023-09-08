# Architecture

![architecture](https://github.com/mariohany98/deploy-5-tier-app-on-k8s-using-minikube/assets/143083001/8eac255a-c462-4f4e-9628-39994946e7ca)

* **Voting App**: A front-end web app in Python which let you vote between two options
* **Result App**: A nodejs webapp which shows the results of the voting in real time
* **Redis**: Is accessed by the voting app to collect new votes
* **PostgresDB**: Is accessed by the result app to read the total count of votes
* **worker**: A .Net Core which reads the count of votes from redis database and update the total count of votes on the postgres database

# Prerequisites

**1-Install kubectl:**

  Follow the instructions on the following link
  
  https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/

**2-Install minikube:**

  Follow the instructions on the following link
  
  https://minikube.sigs.k8s.io/docs/start/

**Note: Minikube provides a pre-configured single-node kubernetes cluster**

**3-Clone this repository to your local machine:**

  git clone https://github.com/mariohany98/deploy-5-tier-app-on-k8s-using-minikube.git

  cd deploy-5-tier-app-on-k8s-using-minikube
  
# Deployment

**1-Deploy the voting app:**

  kubectl create -f voting-app-deployment.yaml
  
  kubectl create -f voting-app-service.yaml

**2-Deploy the redis database:** 

  kubectl create -f redis-deployment.yaml

  kubectl create -f redis-service.yaml

**3-Deploy the postgres database:**

  kubectl create -f postgres-deployment.yaml

  kubectl create -f postgres-service.yaml

 **4-Deploy the worker app:**

  kubectl create -f worker-app-deployment.yaml

 **5-Deploy the result app:**

  kubectl create -f result-app-deployment.yaml

  kubectl create -f result-app-service.yaml

# Access the voting application

**Use the following command to retrieve the URL for the voting application**

 minikube service voting-service --url

 # Access the result application

**Use the following command to retrieve the URL for the result application**

 minikube service result-service --url
