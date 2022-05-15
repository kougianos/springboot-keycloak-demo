This repo showcases the minimum configuration and code required for a Spring boot application to integrate with a Keycloak server.
It is assumed that a Keycloak Server is already set up, and an admin user has been created, in order to perform the steps described below.

Keycloak server steps required:
- Log in to Admin Console
- Create a new realm named {demo}
- Create a new client named {demo-app} with public access type, set its Valid Redirect URIs to * (not recommended for Production services)
- Create a new role with name {user}
- Create a new user with credentials {test}/{test} and assign {user} role

Generate token:
- POST https://20.231.88.141/auth/realms/demo/protocol/openid-connect/token  

Body www-form-urlencoded  

client_id: demo-app  
grant_type: password  
username: test  
password: test
