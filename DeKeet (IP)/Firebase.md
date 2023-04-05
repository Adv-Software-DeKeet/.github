# Firebase

Firebase Auth is a popular authentication service provided by Google's Firebase platform. Here I explain why I choose Firebase and the implemenation.

Firebase Auth provides a secure and reliable way to authenticate users using email/password, Google and other third-party authentication providers. Firebase Auth supports industry-standard security protocols like OAuth2, OpenID Connect, and SSL/TLS encryption to protect user data.

Firebase Auth is easy to integrate and for small applications it is free, which is perfect for me as a student. Firebase provides SDK's and API's to get full control over the service. 

## Authentication and Authorization 

By adding the SDK in my AuthService I can use the Token to authenticate users on my backend. I can set set roles in my backend and I can get the setted roles from the Token Claims to check if user has permission to use the resource. 