### Secrets manager

`aws secretsmanager list-secrets --profile PROFILENAME`
Secret ID will usually be the "Name" value

`aws secretsmanager get-secret-value --secret-id SECRETID --profile PROFILENAME`