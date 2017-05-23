# Docker-Project

3 different Dockerfiles to create following three containers.
Use CentOS/Ubuntu as base images. Don't use readily available
nginx/mysql images
o   Nginx

o   Sample Application written in any language which communicates with DB

o   MySQL Database

Link them all together in such way that, traffic comes on "nginx"
container which forwards to "app" container, which can internally
communicate with "db".


