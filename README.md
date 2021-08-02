# tcp-gateway
Docker based tcp gateway with load-balancing and Service Registry using Spring Boot + Consul + HAProxy


### Built With

This example shows you how to create a microservices architecture with Spring Boot,HAProxy and Consul as service registry.Load Balancing also is provided to enhance the level of optimization.All of microservices are docker based and finally we use Docker Compose to execute our multi-container application.
There is no need to assign static ip-address to each microservice because HAProxy uses Consul as dynamic dns-server.It fetches all services including their health check and addressess via template. 



### Installation

To install this example application, run the following commands:

* npm
  ```sh
  git clone https://github.com/Alirezaeshaqi/tcp-gateway.git
  
  ``` 
This will get a copy of the project installed locally.


To run application you need to follow these steps:

1. open termninal and use `docker load ******.tar` .This will load docker image from existing tar file.
2. To run the client and all the servers,make sure docker-compose is installed on your machine and start containers with command :  `docker-compose up` 



### Prerequisites

In order to run this application you need to install docker and  docker-compose services on your machine.
Its better to use linux distros because they are more handy and also more compatible with docker engine.  
Install docker through this link if your Operating System is Debian based:
   https://docs.docker.com/engine/install/ubuntu/



## Usage


  Its all about routing and load balancing tcp requests.each Tcp requests riches to Ha-proxy host.Since we exposed port number 8888 to 8080  in host.After intercepting TCP request by Ha-proxy,it asks about active instances of microservices via consul Dns Server and routes request to Spring Boot application instances.You can observe load balancing in this senario with round robin strategy.In this mechanism each service registers itself in Consul.Registering each microservice is consist of registering port number 8888 and also management port 8091.It is possible to add Circuit Breaker in this process.HaProxie’s configurations are editable in haproxy.cfg file under /etc/haproxy/haproxy.cfg in docker container.Docker and image configurations are easy to access in docker-compose file.In order to use this stack you need to send some tcp requests to HAProxy’s host through its allocated ip address which is given by docker network.It usually likes 172.17.0.0/16.You can find it out through following command :
  
```docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' container_name_or_id ```

Hope you enjoy it ;)
  
