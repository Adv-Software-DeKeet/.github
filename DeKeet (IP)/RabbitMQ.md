# RabbitMQ

RabbitMQ is a powerful and flexible messaging system that allows applications to communicate with each other reliably and efficiently. It provides a range of features that make it easy to build scalable and reliable messaging applications, and its wide range of APIs and client libraries make it easy to integrate with a wide range of programming languages and environments.

## Messaging
On user registration a POST request is send with user data to the UserService, which stores user data in my MongoDB. As mentioned in portfolio I use Firebase for auth ([Firebase](https://github.com/Adv-Software-DeKeet/.github/blob/main/DeKeet%20(IP)/Firebase.md)). The AuthService communicates with Firebase. To store user data both in my DB and in Firebase, I use RabbitMQ messaging. After registration in my DB a message from UserServive to AuthService  via rabbit

I use RabbitMQ messaging to communicate between my UserService and AuthService. UserService manages user data in MongoDB and AuthService controls Firebase. 
Basic flow:

![basic flow](https://github.com/Adv-Software-DeKeet/.github/blob/main/DeKeet%20(IP)/images/UserRegistration.png)

On user registration UserServices registers in my DB then Rabb from UserService to AuthSer



## Cluster


## Kubernetes
I managed to get RabbitMQ working in local kubernetes. The cluster created earlier is deployed in kubernetes. The cluster of 4 nodes are synchronised which means that if one node gets killed, after reboot the rebooted node synchronises messages from the other nodes, so no history gets lost. To see more detailed information see [RabbitMQ kubernetes](https://github.com/Adv-Software-DeKeet/.github/blob/main/DeKeet%20(IP)/Kubernetes.md)