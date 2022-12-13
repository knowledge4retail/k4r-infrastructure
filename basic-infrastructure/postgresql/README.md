# Read me

## Before installing Postgresql

Before deployment, make sure to create a secret in the same namespace where postgresql is supposed to run:

postgresql-password is the password for your k4r database user as defined in key postgresqlUsername in values.yaml.
postgresql-postgres-password is the password for the default rdbms user postgres.

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: postgresql-passwords
  namespace: <your k4r namespace>
type: Opaque
data:
  postgresql-password: { { <yourAdminPassword> | b64enc | quote } }
  postgresql-postgres-password: { { <yourDatabasePassword> | b64enc | quote } }
```
