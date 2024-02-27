Local db setup
we will create a container for postgresql and enable its extensions.

Manual way:
docker pull postgres
docker run --name some-postgres -p 0:5432 -e POSTGRES_PASSWORD=mysecretpassword -d postgres
docker ps
docker exec -it <mycontainer> bash
apt-get update
apt-get install postgresql-contrib
psql --version
apt install postgresql-16-pgvector
/etc/init.d/postgresql restart
psql -U postgres -c 'create database test;'
psql -U postgres test -c "CREATE EXTENSION vector;"
Via docker container
docker pull ankane/pgvector
docker run --name some-ank -p 0:5432 -e POSTGRES_PASSWORD=mysecretpassword -d ankane/pgvector
docker ps
docker exec -it <mycontainer> bash
psql -U postgres -c 'create database test;'
psql -U postgres test -c "CREATE EXTENSION vector;"
After setting your psql with pgvector you can start using it with lang chain