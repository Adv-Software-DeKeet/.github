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

|  Name |  ------   | usage | min | max | replicas|
|--|--|--|--|--|--|

![AutoScale](https://github.com/Adv-Software-DeKeet/.github/blob/main/DeKeet%20(IP)/images/Autoscale.png)

## Volumes

### Mongo

I created a Persistant volume for my database, so whenever my mongo pods get killed for some reason, the data will not be ereased. Also for scaling. 

![MongoPvc](https://github.com/Adv-Software-DeKeet/.github/blob/main/DeKeet%20(IP)/images/MongoPvc.png)