# This is the deployment version for API Monitoring web application
Source project: https://github.com/nguyentankdb17/CS3
This repository includes only yaml file
## To deploy the web application please do the following instructions:
- Install Docker and Kubernetes on your device. For Kubernetes, I suggest using Minikube for learning purposes. For detailed installation steps, please visit the official websites of [Docker](https://docs.docker.com/) and [Kubernetes](https://kubernetes.io/).
- Check if everything is installed successfully by command `minikube start`, if no errors occur then continue to the next step
- Clone this repository:
  `git clone https://github.com/nguyentankdb17/API_Monitoring_Deployment.git`
- Redirect to the correct folder, and do this following command to deploy the deployments:
  ```
  kubectl apply -f frontend-deploy.yaml
  kubectl apply -f gateway-backend-deploy.yaml
  kubectl apply -f container-status-deploy.yaml
  kubectl apply -f endpoint-status-deploy.yaml
  kubectl apply -f traffic-status-deploy.yaml
  kubectl apply -f system-status-deploy.yaml
  ```
- Check that every pods is created successfully by command `kubectl get pods -o wide`.   
  If all pods are running (as the picture below) you can move to next step, else if any pods fails to be created, try deleting the pod and apply the yaml file again 
- After creating deployments, then create the service to connect them:
  ```
  kubectl apply -f frontend-service.yaml
  kubectl apply -f gateway-backend-service.yaml
  ```
  Check 2 services are created successfully by command `kubectl get svc`
- Everything is set up, now you can get the url to access the web application by command:  `minikube service frontend-service --url`   
  You will get the link and you can access it anywhere, because the frontend service type is NodePort
- Let's explore our product:
