# Keycloak installation instructions

## Before Deploying KeyCloak

Before deployment, make sure to create a secret in the same namespace where keycloak is supposed to be deployed to:

``` yaml
apiVersion: v1
kind: Secret
metadata:
  name: keycloak-passwords
  namespace: <your k4r namespace>
type: Opaque
data:
  admin-password: {{ <yourAdminPassword> | b64enc | quote }}
  database-password: {{ <yourDatabasePassword> | b64enc | quote }}
```  
