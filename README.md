# Build container on jenkins kubernetes agent
```
export REGISTRY_USER=username
export REGISTRY_PASS=password123
export REGISTRY_SERVER=registry.tritec.in
```
```
kubectl create secret docker-registry regcred --docker-username=$REGISTRY_USER --docker-password=$REGISTRY_PASS --docker-server=$REGISTRY_SERVER -n jenkins-agent
```
