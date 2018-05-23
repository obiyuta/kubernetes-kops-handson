# Deploy Containers

* Deploy
* Browse Status

## Deploy

```
$ kubectl apply -f deployments/app.yml
```

## Browse Status

### Pods

```
$ kubectl get po
```

### Containers

```
$ kubectl logs app-deployment-xxxxxxxxxxxxxx [container-name (e.g. app)]
```

### Execute Command

```
$ kubectl exec -it app-deployment-xxxxxxxxxxxxxx [command (e.g. bash)]
```