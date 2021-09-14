---minikube---

-- start minikube
minikube start

-- serve dashboard
minikube dashboard

-- get running services endpoint
minikube service --url basic-nodejs

-- configure minikube // need to run this when using local image
minikube -p minikube docker-env

minikube addons enable metrics-server

for more: https://minikube.sigs.k8s.io/docs/start/
