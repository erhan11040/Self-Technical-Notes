---Setting up postgresql in container---

-- Get image from dockerhub
$ docker pull postgres

-- run container
docker run -p 5432:5432 --name pg-db -e POSTGRES_PASSWORD=PASS -e POSTGRES_USER=USER.NAME -d postgres

-- get inside
docker exec -it pg-db bash
//list available databases witl \l

-- get ip-address of runinng container //we will need this when connecting to db
docker inspect pg-db -f "{{json .NetworkSettings.Networks }}"

-- get pgadmin
$ docker pull dpage/pgadmin4

-- run pgadmin
docker run -p 80:8888 --env PGADMIN_DEFAULT_EMAIL=mail@mail.com --env PGADMIN_DEFAULT_PASSWORD=PASS dpage/pgadmin4

-- Backup your databases
docker exec -t your-db-container pg_dumpall -c -U postgres > dump_`date +%d-%m-%Y"_"%H_%M_%S`.sql
-- Restore your databases
cat your_dump.sql | docker exec -i your-db-container psql -U postgres

for k8s
DUMP
// pod-name         name of the postgres pod
// postgres-user    database user that is able to access the database
// database-name    name of the database
kubectl exec [pod-name] -- bash -c "pg_dump -U [postgres-user] [database-name]" > database.sql

RESTORE
// pod-name         name of the postgres pod
// postgres-user    database user that is able to access the database
// database-name    name of the database
cat database.sql | kubectl exec -i [pod-name] -- psql -U [postgres-user] -d [database-name]