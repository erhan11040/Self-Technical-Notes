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
