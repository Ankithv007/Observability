# Install using Helm

## Add helm repo

`helm repo add prometheus-community https://prometheus-community.github.io/helm-charts`

## Update helm repo

`helm repo update`

## Install helm 

`helm install prometheus prometheus-community/prometheus`

## Expose Prometheus Service

This is required to access prometheus-server using your browser.

`kubectl expose service prometheus-server --type=NodePort --target-port=9090 --name=prometheus-server-ext`

Helm is a package manager for Kubernetes, similar to how apt, yum, or Homebrew work for operating systems. It simplifies the deployment and management of applications on a Kubernetes cluster by using a standardized format called Helm charts
- Key Concepts of Helm:
1. Charts: A Helm chart is a collection of files that describe a set of Kubernetes resources. Think of it as a blueprint for deploying an application or service onto your Kubernetes cluster. Charts contain:
- Kubernetes manifests (YAML files) defining Deployments, Services, ConfigMaps, etc.
- Metadata files (like Chart.yaml and values.yaml).
2.Releases: A release is a specific instance of a chart deployed to a Kubernetes cluster. You can have multiple releases of the same chart, each with its own configuration.
3.Repositories: Helm repositories are collections of Helm charts. They are similar to code repositories like GitHub but specific to Helm charts. Popular repositories include stable, bitnami, and prometheus-community.

my-chart/
  ├── Chart.yaml           # Contains chart metadata (name, version, description, etc.)
  ├── values.yaml          # Default configuration values
  ├── templates/           # Directory with Kubernetes manifest templates (YAML files)
  │   ├── deployment.yaml  # Template for Deployment
  │   ├── service.yaml     # Template for Service
  │   └── _helpers.tpl     # Template helper functions
  ├── charts/              # Directory for chart dependencies
  └── README.md   
  

