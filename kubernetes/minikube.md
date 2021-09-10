---minikube---

-- start minikube
minikube start

-- serve dashboard
minikube dashboard

-- get running services endpoint
minikube service --url basic-nodejs

-- configure minikube
minikube -p minikube docker-env

for more: https://minikube.sigs.k8s.io/docs/start/