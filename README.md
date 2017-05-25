# myjenks 
Dockerized Jenkins app with persistent storage

Docker host built using Ubuntu 16.04 on AWS

to use build image using Dockerfile.

Create named volume poiting to persistent storage accross all swarm nodes.

Run as a service on docker using the following command:

docker service create --name=myjenks \
	--publish 8080:8080/tcp --publish 50000:50000/tcp \
	--mount=type=bind,src=/var/run/docker.sock,dst=/var/run/docker.sock \
	--mount=type=bind,src=$(which docker),dst=/usr/bin/docker \
	--mount type=volume,source=<named_volume>,destination=/var/jenkins_home,volume-nocopy=1 \
	<docker_registry>/engineering/myjenks
