az login
//login to azure

az account set --subscription "Project Azure Subscription"
//set azure subscription

az aks get-credentials -a --resource-group rg-dev-project --name aks-dev-proj

az aks browse --resource-group rg-dev-proj --name aks-dev-proj
//open dashboard

az aks list --resource-group rg-dev-proj

az network public-ip create  --resource-group rg-dev-proj  --name aks-test-ip  --allocation-method static

az network public-ip create  --resource-group xxx_rg-dev-proj_aks-dev-proj_xxxxx  --name aks-test-ip  --allocation-method static

curl ifconfig.me. //get ip from server

install kube dashboard

kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.3.1/aio/deploy/recommended.yaml
kubectl proxy
http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/#/login