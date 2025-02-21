# How to deploy app
## Prerequisites
1. Install [Minikube](https://minikube.sigs.k8s.io/docs/)
2. Install [kubectl](https://kubernetes.io/ru/docs/tasks/tools/install-kubectl/)
3. Install [helm](https://helm.sh/)

## Steps 
1. run minikube 
2. kubectl set context minikube
3. Deploy PostgreSQL\
3.1 `helm install my-release oci://registry-1.docker.io/bitnamicharts/postgresql --set auth.postgresPassword=<supersecurepassword>`\
3.2 find name of db in kubernetes `kubectl get svc`
4. Create secrets\
    4.1 create .env file from .env.example file\
    4.2 fill .env file, using same `<supersecurepassword>` as u did when deploy DB
    4.3 run command `kubectl create secret generic test-django-app-secret --from-env-file=.env`
5. run `kubectl apply -f .\deployment\deployment.yaml` 
6. run `kubectl apply -f .\deployment\migration.yml` 
7. run `kubectl apply -f .\deployment\service.yml` 
8. run `kubectl apply -f .\deployment\ingress.yml` 
9. run `kubectl apply -f .\deployment\clear-session.yml` 