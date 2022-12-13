# K4R Fridge installation instructions

## Before Deploying K4R Fridge

Before deployment, make sure to create a secret in the same namespace where k4r-fridge is supposed to be deployed to:

``` yaml
apiVersion: v1
kind: Secret
metadata:
  name: opp-api-key
  namespace: <your k4r namespace>
type: Opaque
data:
  api-key: {{ <yourPricingApiKey> | b64enc | quote }}
```  
