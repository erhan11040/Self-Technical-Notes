helm install nginx-ingress stable/nginx-ingress --namespace dev \--set controller.replicaCount=2 \--set controller.nodeSelector."beta\.kubernetes\.io/os"=linux \--set defaultBackend.nodeSelector."beta\.kubernetes\.io/os"=linux

helm uninstall nginx-ingress --namespace test

helm repo add stable https://kubernetes-charts.storage.googleapis.com/

helm install nginx-ingress stable/nginx-ingress --namespace dev  --set controller.replicaCount=2 --set controller.nodeSelector."beta\.kubernetes\.io/os"=linux --set defaultBackend.nodeSelector."beta\.kubernetes\.io/os"=linux

helm uninstall nginx-ingress --namespace uat


helm install nginx-ingress stable/nginx-ingress --namespace dev -f internal.yaml --set controller.replicaCount=2 --set controller.nodeSelector."beta\.kubernetes\.io/os"=linux --set defaultBackend.nodeSelector."beta\.kubernetes\.io/os"=linux

helm install nginx-ingress stable/nginx-ingress \
    --namespace ingress-basic \
    -f internal-ingress.yaml \
    --set controller.replicaCount=2 \
    --set controller.nodeSelector."beta\.kubernetes\.io/os"=linux \
    --set defaultBackend.nodeSelector."beta\.kubernetes\.io/os"=linux