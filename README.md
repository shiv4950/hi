# maven docker basics

sudo apt update

sudo apt install openjdk-11-jdk -y

maven archieve select version-binaries-apache 

maven copy link address -goto bash

wget link

ls 

tar -xvzf filename

lss

cd filename

ls

cd bin

ls

apt install maven -y

mvn --v

goto git hub

copy clone address

git clone address

ls

goto pom.xml

mvn validate

mvn test

ls

ls target

mvn clean

mvn install

ls

ls target

# docker commands

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


# git

1) initialize git "git init"

2) add acc "git config --global username accountname"  "git config --global username email add"

3) create repository

4) open vs under git bash clone repsitory "git clone repositoru url"

5) in vs editor change the readme.md file  add<h1> tag "<h1>something<h1>"

6) add file "git add README.md"

7) commit changes "git commit -m"

8) push file in repo "git push"

9) create new txt file "touch newfile.txt" then add,commit,push

10) modify the text file using any text editor commit changes and push repo

11) create iss53 branch "git branch iss53"



12) "git checkout iss53" "git push origin iss53"

13) create index.html in iss53 "touch index.html" and also update readme.md file in the iss53 branch then commit and push the changes on git repoi

14) difference "git log" for find hashes then copy c1 hash and c2 hash and paste it in "git diff c1.hash c2.hash" command as well as use command "git diff main iss53"

# hotfix 

1) create hotfix "git branch hotfix"

2) git checkout hotfix

3) touch new.txt

4) git branch origin hotfix

5) commit changes and push the new.txt in repo

6) merge "git checkout main" "git merge hotfix"  "git push origin --delete hotfix"

7) merge iss53 "git checkout main"

8) "git merge iss53"

9) git push origin --delete iss53
   
