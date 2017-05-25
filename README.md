# myjenks 
Dockerized Jenkins app with persistent storage

to use build image using Dockerfile.

Run as a service on docker using the following command:

docker service create --name=myjenks --publish 8080:8080/tcp --publish 50000:50000/tcp --mount=type=bind,src=/var/run/docker.sock,dst=/var/run/docker.sock --mount type=volume,source=<named_volume>,destination=/var/jenkins_home,volume-nocopy=1 <DTR_host_address>/engineering/myjenks
