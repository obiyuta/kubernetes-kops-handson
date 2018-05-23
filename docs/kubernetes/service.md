# Manage Services

* Configure ELB
* Apply

## Configure ELB

```
apiVersion: v1
kind: Service
metadata:
  name: app-elb-service
  annotations:
    service.beta.kubernetes.io/aws-load-balancer-backend-protocol: http
    service.beta.kubernetes.io/aws-load-balancer-ssl-cert: arn:aws:acm:ap-northeast-1:xxxxxxx:certificate/xxxxxxxxxxxxxxxx
    service.beta.kubernetes.io/aws-load-balancer-ssl-ports: "https"
spec:
  type: LoadBalancer
  selector:
    app: app
  ports:
  - port: 80
    name: http
    protocol: TCP
    targetPort: backend-http
  - port: 443
    name: https
    protocol: TCP
    targetPort: backend-http
```

## Apply

```
$ kubectl apply -f services/app.yml
```