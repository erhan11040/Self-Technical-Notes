az login
//login to azure

az account set --subscription "Project Azure Subscription"
//set azure subscription

az aks get-credentials -a --resource-group rg-dev-project --name aks-dev-proj

kubectl config set-context --current --namespace=dev
///set Name space above 

az aks browse --resource-group rg-dev-proj --name aks-dev-proj
//open dashboard

az aks list --resource-group rg-dev-proj

az network public-ip create  --resource-group rg-dev-proj  --name aks-test-ip  --allocation-method static

az network public-ip create  --resource-group xxx_rg-dev-proj_aks-dev-proj_xxxxx  --name aks-test-ip  --allocation-method static

curl ifconfig.me. //get ip from server