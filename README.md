Keycloak steps:
- Log in to Admin Console
- Create a new realm named demo
- Create a new client named demo-app with public access type, set its Valid Redirect URIs to * (not recommended for Production services)
- Create a new role with name "user"
- Create a new user with credentials test/test and assign "user" role

Generate token:
- POST https://20.231.88.141/auth/realms/demo/protocol/openid-connect/token  

Body www-form-urlencoded  

client_id: demo-app  
grant_type: password  
username: test  
password: test






