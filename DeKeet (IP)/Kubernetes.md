# Kubernetes

Kubernetes allows you to easily manage and scale containerized applications across multiple hosts and clusters, while ensuring high availability and resilience. It provides a wide range of features, such as automatic container deployment and scaling, load balancing, self-healing, service discovery, and rolling updates.

## Services deployment
Deployed AuthService and UserService in local kubernetes cluster. ![kubernetes](https://github.com/Adv-Software-DeKeet/.github/blob/main/DeKeet%20(IP)/images/KubernetesPods.png)

## API Gateway
To access API, Ingress is used and address is: localhost:9080/api/{svc}

UserService: localhost:9080/api/user

AuthService: not reachable for externally (yet?)

## RabbitMQ
Rabbit Cluster in kubernetes:

![RabbitCluster](https://github.com/Adv-Software-DeKeet/.github/blob/main/DeKeet%20(IP)/images/RabbitCluster.png)

Messaging between services AuthService and UserService works in local kubernetes.

## Autoscaling

I am able to autoscale pods based on CPU usage. I am requesting an x amount of cores per pod. when pod is at 95% core usage it will scale up to max 10 pods. When usage cools down it scale down to 1 pod. This process can be seen below, as I loadtested my user API:

|  Name |  ------   | CPU usage | min | max | replicas|
|--|--|--|--|--|--|

![AutoScale](https://github.com/Adv-Software-DeKeet/.github/blob/main/DeKeet%20(IP)/images/Autoscale.png)


it starts with one replica and you can see the usage exceding the 95%, so it scales up that point. It peaks at 5 replicas then it was able to handle all the request with a usage below 95%. After I stopped the loadtesting, the usage drops and it scales down to 1 replica again.

## Monitoring

For monitoring I use Prometheus and Grafana. As seen in the picture below.

![Montiroing](https://github.com/Adv-Software-DeKeet/.github/blob/main/DeKeet%20(IP)/images/Monitoring.png)

## Volumes

### Mongo

I created a Persistant volume for my database, so whenever my mongo pods get killed for some reason, the data will not be ereased. Also for scaling. 

![MongoPvc](https://github.com/Adv-Software-DeKeet/.github/blob/main/DeKeet%20(IP)/images/MongoPvc.png)

## ResourceMapping

![RM](https://github.com/Adv-Software-DeKeet/.github/blob/main/DeKeet%20(IP)/images/RM.png)

Given the information, my primary focus is to  scale the services in my Keet applications. By efficiently scaling these services, I can ensure faster response times and handle increased traffic effectively. To achieve this, I have devised the following steps:

- Scaling Services: I will carefully assess the scalability requirements of the services in my Keet application. Based on the application's needs, I will determine whether horizontal scaling (adding more instances) or vertical scaling (increasing resources of existing instances) is the most suitable approach.

- Optimizing User Service: I will conduct a thorough analysis of the User service to identify any performance bottlenecks. By optimizing database queries, implementing efficient caching mechanisms for frequently accessed user data, and enhancing the service's ability to handle concurrent requests, I can significantly improve its overall performance.

- Enhancing Auth Service: As the Auth service is critical for security and authentication, I will prioritize its performance improvements. This includes implementing token-based authentication mechanisms and exploring efficient session management techniques to streamline authentication and authorization processes.

- Load Balancing Strategies: To ensure consistent performance and prevent overload on any single instance, I will implement load balancing mechanisms specifically for the services. These mechanisms will evenly distribute incoming requests across multiple instances.

- Monitoring and Alerting Systems: I will establish comprehensive monitoring and alerting systems dedicated to the services using Prometheus from Google Cloud. This will allow me to proactively identify and address any potential issues or anomalies, ensuring optimal performance and timely response to any incidents.

- Database Optimization: I will carefully evaluate the database performance of the services. This involves analyzing query execution plans, optimizing indexes, and considering scaling the database infrastructure if necessary. These measures will enable efficient data access and handling of increased load.

- Automated Scaling: To facilitate dynamic scalability in response to real-time demand, I will explore automated scaling mechanisms based on predefined metrics or thresholds. This will eliminate the need for manual intervention and ensure seamless scalability as the application grows.

- Security Considerations: Given the sensitivity of user information, I will prioritize maintaining the security of the services. I will review and enhance security measures, including access controls, encryption, and protection against common security vulnerabilities, ensuring that scaling efforts do not compromise application security.

By regularly assessing and fine-tuning these scaling strategies as my Keet applications grows and user demands evolve, I can optimize its performance, ensure scalability, and deliver an exceptional user experience. Continuous resource mapping analysis and monitoring will play a crucial role in achieving these goals while maintaining the desired level of performance and security.