# Security & Design



## Secrets

I use github secrets.

## ENV

I use ENV variables for developing and production. So sensitive data will be available to the public.

E.g. GCloud (Google Cloud) key is stored in an env locally and in kubernetes envirement a Secret with the key is made and mounted into the application.

## SSL 

With HTTPS, data is encrypted in transit in both directions: going to and coming from the origin server. The protocol keeps communications secure so that malicious parties can't observe what data is being sent. 

I have setup [GCloud kubernetes](https://github.com/Adv-Software-DeKeet/.github/blob/main/DeKeet%20(IP)/GCloud.md). Now by default it uses HTTP. I created SSL certificates with Google-managed certificate. Now it uses HTTPS:

