# K4R DT-API

## Before Deploying K4R DT-API

Before deployment, make sure to create a secret in the same namespace where k4r-dt-api is supposed to be deployed to:

``` yaml
apiVersion: v1
kind: Secret
metadata:
  name: k4r-storage-secret
  namespace: <your k4r namespace>
type: Opaque
data:
  blobstorageconnectionstring: {{ <yourPricingApiKey> | b64enc | quote }}
```  
