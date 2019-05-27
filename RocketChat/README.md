Deploy RocketChat whit docker-compose and load balancing 
Requirement :
	Docker and Docker-Compose:
		https://docs.docker.com/install/
Get started :
1 - copy  RocketChat folder from repo (or Clone). that include "docker-compose.yml" and "nginx.conf" file.
2 - in "docker-compose.yml" edit ROOT_URL to match your domain name or IP address (in rocketchat1 and rocketchat2 section)
3 - in "nginx.conf" edit server address (in "upstream LB1" section) to match your IP address.
4 - Start the mongodb server by:
		docker-compose up -d mongo
5 - The first time you start mongo, you’ll also need to initialize it before being able to use Rocket.Chat. Ensure that mongo is in the running state, then:
		docker-compose up -d mongo-init-replica
6 - Once you’re sure that mongodb is up and running:
		docker-compose up -d rocketchat1
	then:
		docker-compose up -d rocketchat2
7 - for load balancing by nginx:
		docker-compose up -d nginx
8 - test it in browser http://Your-IP-Address:3000/

*** This is a solution for deploying on a server, But to better load balance, multiple servers should be used (with docker swarm)
