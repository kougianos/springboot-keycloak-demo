## Spring Boot & Keycloak demo application
This repo showcases the minimum configuration and code required for a Spring boot application to integrate with a Keycloak server.
It is assumed that a Keycloak Server is already set up, and an admin user has been created, in order to perform the steps described below.

**Keycloak server steps required:**
1. Log in to Admin Console
2. Create a new realm named {demo}
3. Create a new client named {demo-app} with public access type, set its Valid Redirect URIs to http://localhost:8080/*
4. Create a new role with name {user}
5. Create a new user with credentials {test}/{test} and assign {user} role

The Keycloak server used in this app is deployed on https://20.231.88.141

---

Now that we have set up everything required on the Keycloak Server side, we need to generate an access token that will be used as an Authentication Header.

**Generate token (using Postman):**  
POST https://20.231.88.141/auth/realms/demo/protocol/openid-connect/token  

```
Body: www-form-urlencoded  

client_id: demo-app  
grant_type: password  
username: test  
password: test
```

![image](https://user-images.githubusercontent.com/23719920/168478283-f941224d-8a28-4dc6-8c35-93f2c886d814.png)

**Use token to access /hello endpoint which requires authenticated user (using Postman):**  
GET http://localhost:8080/hello
```
Authorization: Bearer {access_token_from_POST_request}
```

![image](https://user-images.githubusercontent.com/23719920/168478554-18d5b20c-269d-4609-a13f-940bc0cf1c90.png)
