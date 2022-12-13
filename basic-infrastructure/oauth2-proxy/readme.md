# README

## Before deploying oauth2-proxy

Before deployment, create a secret:

``` yaml
apiVersion: v1
kind: Secret
metadata:
  name: oauth2-proxy
  namespace: <your k4r namespace>
type: Opaque
data:
  cookie-secret: {{ <random 32 character string> | b64enc | quote }}
  client-secret: {{ <not required but needs to be filled, make something up> | b64enc | quote }}
  client-id: {{ <your k4r client in oidc provider, k4r-test in keycloak during project phase> | b64enc | quote }}
```
