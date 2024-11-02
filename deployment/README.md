
## How to add secrets
to add secrets you have to create kubernetes secrets 
to do this: 
1. create .env file from .env.example file 
2. fill .env file 
3. run command `kubectl create secret generic test-django-app-secret --from-env-file=.env`