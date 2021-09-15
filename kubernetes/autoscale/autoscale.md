---ENABLE METRİCS---

// install metrics server -latest
kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml

//or

// install metrics server - high availablty
kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/high-availability.yaml

//then 
minikube addons enable metrics-server

----AUTOSCALE---

//deploy your app
kubectl apply -f https://k8s.io/examples/application/php-apache.yaml

//after deployment
kubectl autoscale deployment php-apache --cpu-percent=50 --min=1 --max=10

//check if it is working
kubectl get hpa

--- LOAD GENERATOR ---

//create a load generator  for test
kubectl run -i --tty load-generator --image=busybox /bin/sh

//if pod exists use this
kubectl attach load-generator -c load-generator -i -t

//find your service ip address & endpoint
//in bash 
while true; do wget -q -O- http://php-apache; done

//note do not forget to delete this pod after you are done

----RESULTS---

//watch current state
kubectl get hpa --watch

//watch events
kubectl describe hpa

