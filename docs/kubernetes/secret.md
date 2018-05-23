# Manage Secret Envars

* Apply
* Browse
* Delete
* Use from Container

## Apply

```
$ kubectl apply -f secrets/app.yml
$ kubectl apply -f secrets/rds.yml
```

## Browse

```
$ kubectl get secret app-secrets -o yaml
$ kubectl get secret rds-credentials -o yaml
```

## Delete

```
$ kubectl delete -f secrets/app.yml
```

## Use from Container

Refer from deployment configuration as `env` like the below.

```
containers:
- name: your-container
  env:
    - name: SECRET_ACCESS_TOKEN
      valueFrom:
        secretKeyRef:
          name: app-secrets
          key: secret_access_token
```