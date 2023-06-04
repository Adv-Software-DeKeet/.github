# Security & Design



## Secrets

I use github secrets for github. For Google Cloud I use the default secret variables available in the pipeline.

## ENV

I use ENV variables for developing and production. So sensitive data will be available to the public.

E.g. GCloud (Google Cloud) key is stored in an env locally and in kubernetes envirement a Secret with the key is made and mounted into the application.

## SSL 

With HTTPS, data is encrypted in transit in both directions: going to and coming from the origin server. The protocol keeps communications secure so that malicious parties can't observe what data is being sent. 

I have setup [GCloud kubernetes](https://github.com/Adv-Software-DeKeet/.github/blob/main/DeKeet%20(IP)/GCloud.md). Now by default it uses HTTP. I created SSL certificates with Google-managed certificate. Now it uses HTTPS:

![ssl](https://github.com/Adv-Software-DeKeet/.github/blob/main/DeKeet%20(IP)/images/Ssl.png)

Config gcloud: 

![gcloudssl](https://github.com/Adv-Software-DeKeet/.github/blob/main/DeKeet%20(IP)/images/sslGcloud.png)

## Securing by Role (RBAC)

I protect my endpoints with roles so I have default, host and admin roles in my system. The default role is what every user gets by default they can only manage their own data. An user with host role can inititate events in the system and manage their own events. Admins can manage everything in the system.

## Secure by Id

In my system it is not possible to manage data from another user. You can only manage data that is yours. When you make a request and inctercept it and edit the user Id, you are still not able to change or access data. The only way you can manage data from other users is when u are able to manipulate JWT tokens.

## noSql Injection

I use MongoDB a noSql DataBase. Injections are still present to happen. I use spring mongoDB dependency which automaticaly sanitizes the queries.