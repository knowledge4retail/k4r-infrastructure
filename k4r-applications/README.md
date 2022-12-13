K4R Applications
=================

This folder contains multiple helm charts to deploy k4r developed applications.

IMPORTANT
____________

Before deploying any of the k4r applications, make sure to fill the contents of the `../config/k4r-passwords.yaml` with a `base64` encoded strings containing the different passwords to run the k4r applications and then create the secret in your target namespace.

```bash

# Get a base64 strings representation of your passwords
## make sure to include -n as echo parameter. This eliminates the output of the trailing newline
echo -n "yourPasswordAsABase64String" | base64
echo -n "your2ndPasswordAsABase64String" | base64

# edit the file k4r-passwords and update it with the base64 values you got for the passwords
# and then run:

kubectl apply -f k4r-passwords.yaml -n $DEPLOYMENT_NAMESPACE
```

The same thing also applies for application specific secrets e.g. `k4r-dt-api` or `k4r-fridge`.

More information on this could be found in the corresponding charts.
