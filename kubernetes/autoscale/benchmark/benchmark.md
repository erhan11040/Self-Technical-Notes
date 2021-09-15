--TEST ENV---
kubectl create namespace non-scale
kubectl apply -f php-apache.yaml --namespace non-scale
kubectl apply -f infinite-calls.yaml --namespace non-scale
kubectl scale --replicas=4 deployment/infinite-calls.yaml --namespace non-scale
//then start you measurements 
//i have used this (https://github.com/erhan11040/AvarageResponseTimeMeasurement) to measure response times
//check autoscale.md to create auto scale php-apache app

//scale app : 1-10 pods
//non-scale app : 1 pod
//pods are identical only auto scaling enabled on "scale app"

---non-scale---TEST1---
infinite-calls replica : 4
avarage response : 1080.73
time elapsed : 1:10.56
successfull : 66
failed : 0
total : 66

----scale----TEST1----
infinite-calls replica : 4
avarage response : 349.37
time elapsed : 1:0.65
successfull : 173
failed : 0
total : 173

------non-scale--TEST2---
infinite-calls replica : 8
avarage response : 2151.1
time elapsed : 1:1.99
successfull : 30
failed : 0
total : 30

-------scale--TEST2---
infinite-calls replica : 8
avarage response : 743.1
time elapsed : 1:0.37
successfull : 83
failed : 0
total : 83