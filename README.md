# docker-on-mint
installing docker on mint

https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-compose-on-ubuntu-14-04

restart is necessary for docker to start

When running non-interactive
docker run -d -P -v $(pwd):/home/$USER/foo \
-e USER=$USER  -e USERID=$UID <name_of_image>

When running interactive
docker run --rm -it --user docker -v $(pwd):/home/docker/foo -w /home/docker/foo hello-world bash

docker run --rm -it -v $(pwd):/home/$USER/foo -e USER=$USER  -e USERID=$UID hello-world bash

Then I found this link describing data containers - aha moment

https://medium.com/@ramangupta/why-docker-data-containers-are-good-589b3c6c749e#.nyj1eaqiq

best practice is to access data only from containers to maintain portability

docker run -v /foo --name="vtest" busybox \
  sh -c 'echo hello docker volume > /foo/testing.txt'
  
and to read...

docker run --volumes-from=vtest busybox cat /foo/testing.txt
hello docker volume

http://container-solutions.com/understanding-volumes-docker/

Another solution for sharing data over bittorrent is

https://jaxenter.com/how-to-share-docker-volumes-across-hosts-119602.html


