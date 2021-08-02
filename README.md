# tcp-gateway
docker based tcp gateway with load-balancing architecture using spring boot+consul+haproxy


### Built With

This example shows you how to create a microservices architecture with Spring Boot,Ha-Proxy and Consul as service registry.Load Balancing also is provided to enhance the level of optimization.All of microservices are docker based and finally we use docker-compose to execute our multi-container application.
There is no need to assign static ip-address to each microservice because ha-proxy uses consul as dynamic dns-server.It fetches all services including their health check and address via template. 


### Installation

To install this example application, run the following commands:

* npm
  ```sh
  
