# Security & Design



## Secrets

I use github secrets.

## ENV

I use ENV variables for developing and production. So sensitive data will be available to the public.

E.g. GCloud (Google Cloud) key is stored in an env locally and in kubernetes envirement a Secret with the key is made and mounted into the application.