to connect already deployed postgres service:
--list services
kubectl get svc postgres

psql -h localhost -U testadmin --password -p 31070 testdb
-- then enter the password
test123

if you want to connect via pgadmin or smtng else
use load balancer as service , which will expose service for external use
