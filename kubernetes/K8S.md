KUBERNETES NOTES

az login
//login to azure

az account set --subscription "Project Azure Subscription"
//set azure subscription

az aks get-credentials -a --resource-group rg-dev-project --name aks-dev-proj

kubectl config set-context --current --namespace=dev
///set Name space above 

az aks browse --resource-group rg-dev-proj --name aks-dev-proj
//open dashboard

kubectl get services --namespace=dev
//list of services

kubectl get pods 
//get pod list

kubectl get pod mypod
//get selected pod

kubectl exec --stdin --tty nginx-ingress-controller-xxxx-xx -- /bin/bash
//get console

kubectl exec -i -t dev-proj-fe-xxxxx-xxxx --container dev-proj-fe -- /bin/bash
//get console if pod has more then1 container

kubectl get nodes -o wide


kubectl run my-nginx --image=nginx --replicas=2 --port=80
//The kubectl run line above will create two nginx pods listening on port 80. 
It will also create a deployment named my-nginx to ensure that there are always two pods running.

kubectl expose deployment my-nginx --port=80 --type=LoadBalancer
//creating external ip address

kubectl get services --watch
//realtime services watch

kubectl create -f basic-pod.yaml
//create pod from yaml

kubectl create -f basic-deployment.yaml
//deploy pod

kubectl expose deployment basic-deployment --port=80 --type=LoadBalancer
//exposed to internet
TERMİNOLOJİ
pods=>group of container
Node=> container
Namespace=> group of pods


helm install nginx-ingress stable/nginx-ingress --namespace dev \--set controller.replicaCount=2 \--set controller.nodeSelector."beta\.kubernetes\.io/os"=linux \--set defaultBackend.nodeSelector."beta\.kubernetes\.io/os"=linux

helm uninstall nginx-ingress --namespace test

kubectl delete -f hw1.yaml --namespace newerhan
kubectl apply -f hw1.yaml --namespace dev
kubectl apply -f hw2.yaml --namespace dev
kubectl apply -f ingress-dev.yaml --namespace dev

kubectl delete -f hw2.yaml --namespace dev
kubectl delete -f ingress.yaml --namespace dev
kubectl delete namespace dev

kubectl create namespace newproj
helm repo add stable https://kubernetes-charts.storage.googleapis.com/

helm install nginx-ingress stable/nginx-ingress --namespace dev  --set controller.replicaCount=2 --set controller.nodeSelector."beta\.kubernetes\.io/os"=linux --set defaultBackend.nodeSelector."beta\.kubernetes\.io/os"=linux

KIND=deployment
NAME=my-app-staging
RELEASE=staging
NAMESPACE=newerhan
kubectl annotate deployment stable meta.helm.sh/release-name=staging
kubectl annotate  meta.helm.sh/release-namespace=newproj
kubectl label deployment my-app-staging app.kubernetes.io/managed-by=Helm

kubectl delete clusterrole nginx-ingress

kubectl delete clusterrolebinding nginx-ingress
helm uninstall nginx-ingress --namespace uat


helm install nginx-ingress stable/nginx-ingress --namespace dev -f internal.yaml --set controller.replicaCount=2 --set controller.nodeSelector."beta\.kubernetes\.io/os"=linux --set defaultBackend.nodeSelector."beta\.kubernetes\.io/os"=linux

helm install nginx-ingress stable/nginx-ingress \
    --namespace ingress-basic \
    -f internal-ingress.yaml \
    --set controller.replicaCount=2 \
    --set controller.nodeSelector."beta\.kubernetes\.io/os"=linux \
    --set defaultBackend.nodeSelector."beta\.kubernetes\.io/os"=linux

    kubectl edit svc   servn 

    az aks list --resource-group rg-dev-proj


kubectl create clusterrolebinding kubernetes-dashboard --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
//update dashboard priviligences

//skip login
kubectl edit deployment/kubernetes-dashboard --namespace=kube-system
//add this=>  --enable-skip-login


------TO GET BEARER TOKEN INCASE OF NEEED----
kubectl -n kube-system get secret
//get lis tof services
//choose one
kubectl -n kube-system describe secret deployment-controller-token-xxx
deployment-controller-token-s8rrv

service-account-controller-token-xxx
kubectl config set-credentials cluster-admin --token=


kubectl -n kube-system describe secret $(kubectl -n kube-system get secret | awk '/^deployment-controller-token-/{print $1}') | awk '$1=="token:"{print $2}'

az network public-ip create  --resource-group rg-dev-proj  --name aks-test-ip  --allocation-method static

az network public-ip create  --resource-group xxx_rg-dev-proj_aks-dev-proj_xxxxx  --name aks-test-ip  --allocation-method static

kubectl apply -f engress.yaml --namespace test
kubectl delete -f engress.yaml --namespace test

curl ifconfig.me. //get ip from server