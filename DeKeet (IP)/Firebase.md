# Firebase

Firebase Auth is a popular authentication service provided by Google's Firebase platform. Here I explain why I choose Firebase and the implemenation.

Firebase Auth provides a secure and reliable way to authenticate users using email/password, Google and other third-party authentication providers. Firebase Auth supports industry-standard security protocols like OAuth2, OpenID Connect, and SSL/TLS encryption to protect user data.

Firebase Auth is easy to integrate and for small applications it is free, which is perfect for me as a student. Firebase provides SDK's and API's to get full control over the service. 

## Authentication and Authorization 

By adding the SDK in my AuthService I can use the Token to authenticate users on my backend. 

```
FirebaseAuth.getInstance().verifyIdToken(token);
```

With the above code I can authenticate users and protect my resources from unauthorized users.

I can set set roles in my backend and I can get the setted roles from the Token Claims to check if user has permission to use the resource. 

E.g. The admin has role "admin" and can manage all the users. If I don't check the incoming request by "admin" role, the black hacker is in a worst case scenario able to delete all the users in my platform. 

To prevent the above from happening the following can be done:
```
// Verify the ID token first.
FirebaseToken decoded = FirebaseAuth.getInstance().verifyIdToken(token);
if (Boolean.TRUE.equals(decoded.getClaims().get("admin"))) {
  // Allow access to requested admin resource.
}
```

With the above code I can protect my resources based on roles.

For full code look in my repository: [AuthService](https://github.com/Adv-Software-DeKeet/DeKeet-AuthService)