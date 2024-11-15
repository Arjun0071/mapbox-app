# mapbox-app
This repository contains the necessary files to deploy a Mapbox-based application using Helm on a Minikube cluster. The application utilizes Kubernetes resources such as services, deployments, configmaps, and Helm charts for easy deployment and management.

Directory Structure
charts/: Contains the Helm chart for the application.
service.yaml: Defines the Kubernetes service for the application.
deployment.yaml: Specifies the deployment configuration.
configmap.yaml: Stores configuration values, including the Mapbox API key.
values.yaml: Defines default values for the Helm chart.
Prerequisites
Install Minikube.
Install Helm.
Ensure kubectl is installed and configured to interact with the Minikube cluster.
Instructions
1. Start Minikube
Start the Minikube cluster using the following command:

minikube start  
2. Add the Mapbox API Key
Add your Mapbox API key to the configmap.yaml file before deployment:
apiVersion: v1
kind: ConfigMap
metadata:
  name: mapbox-config
data:
  MAPBOX_API_KEY: "your-mapbox-api-key"
3. Deploy Using Helm
Initialize Helm in your cluster (if not already done):

helm repo add stable https://charts.helm.sh/stable
helm repo update  
Install the application Helm chart:

bash
Copy code
helm install mapbox-app ./charts  
4. Verify Deployment
Check the status of your application using:

kubectl get pods  
kubectl get services  
5. Access the Application
Expose the service to access the application:

minikube service mapbox-app  
About the Application
This application leverages Mapbox to provide mapping services. The Mapbox API key is a critical component and must be added to the ConfigMap before deploying the application.
