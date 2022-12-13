# MongoDB installation instructions

## Before Deploying MongoDB

Before deployment, make sure to create a secret in the same namespace where mongodb is supposed to run:

``` yaml
apiVersion: v1
kind: Secret
metadata:
  name: mongodb-passwords
  namespace: <your k4r namespace>
type: Opaque
data:
  mongodb-root-password: {{ <yourAdminPassword> | b64enc | quote }}
  mongodb-password: {{ <yourDatabasePassword> | b64enc | quote }}
```  

## Accessing mongodb container

```bash
## access mongo container
kubectl run --namespace NAMESPACE mongodb-client --rm --tty -i --restart='Never'  --image docker.io/bitnami/mongodb:4.4.4-debian-10-r0 --command -- bash
### then from bash to access a db (e.g. roslog) with username -u and password -p
mongo --host "mongodb" --authenticationDatabase roslog -u k4r -p k4r
```
