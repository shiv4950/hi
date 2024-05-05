# maven docker basics


docker commands

sudo docker pull ubuntu:20.04

sudo docker images

sudo docker pull ubuntu:latest

sudo docker image rm ubuntu:20.04

sudo docker run --name ubuntu-os -it -d ubuntu:20.04

sudo docker run --name ubuntu-os -it -d ubuntu:20.08

sudo docker container stop(cid)

sudo docker container restart(cid)

sudo docker ps -a

sudo docker container exec -d (cid) mkdir css

sudo docker container exec -it (cid) ls

sudo docker container stop (cid)

sudo docker container prune

# postgresql
sudo docker pull postgres:latest

sudo docker run --name some-postgres -e POSTGRES_PASSWORD=mysecretpassword -d postgres

sudo docker ps -a

sudo docker container exec -it some-postgres sh

#psql  -U postgres

create database ss

sudo docker container stop (Id)
