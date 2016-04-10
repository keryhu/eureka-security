#spring-cloud-eureka-security-problems


I study spring cloud eureka , cloud and they works finely . But after adding security in eureka service , it met some errors .

The eureka service application.yml

	security:
	  user:
	    name: user
	    password: password
	
	eureka: 
	  client:
	    registerWithEureka: false
	    fetchRegistry: false
	  server:
	    wait-time-in-ms-when-sync-empty: 0 

And The config-service application.java

	@SpringBootApplication
	@EnableConfigServer
	@EnableDiscoveryClient

config-service application.yml

	eureka:
	  client:
	    registry-fetch-interval-seconds: 5
	    serviceUrl:
	       defaultZone: http://user:password@${domain.name:localhost}:8761/eureka/
	  
	spring:  
	  cloud:
	     config:
	       server:
	         git:
	           uri: https://github.com/spring-cloud-samples/config-repo
	           basedir: target/config 

There is errors exported after starting the config-service:

