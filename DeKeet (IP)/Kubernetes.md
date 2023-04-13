# Kubernetes

Kubernetes allows you to easily manage and scale containerized applications across multiple hosts and clusters, while ensuring high availability and resilience. It provides a wide range of features, such as automatic container deployment and scaling, load balancing, self-healing, service discovery, and rolling updates.

## Services deployment
Deployed AuthService and UserService in local kubernetes cluster. ![kubernetes](https://github.com/Adv-Software-DeKeet/.github/blob/main/DeKeet%20(IP)/images/KubernetesPods.png)

## API Gateway
To access API, Ingress is used and address is: api.localhost:9080

UserService: api.localhost:9080/user

AuthService: api.localhost:9080/auth

## RabbitMQ
Rabbit Cluster in kubernetes:

![RabbitCluster](https://github.com/Adv-Software-DeKeet/.github/blob/main/DeKeet%20(IP)/images/RabbitCluster.png)

Messaging between services AuthService and UserService works in local kubernetes.

## Autoscaling

![AutoScale](https://github.com/Adv-Software-DeKeet/.github/blob/main/DeKeet%20(IP)/images/Autoscale.png)