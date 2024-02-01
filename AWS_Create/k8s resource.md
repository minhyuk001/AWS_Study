```
kubectl apply -f <filename>
```

### Resource Info Get
```
kubectl get <resource> -n <namespace>
```

### Deployment
```yaml
deployment.yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: <NAME>
spec:
  selector:
    matchLabels:
      run: nginx
  replicas: 2
  template:
    metadata:
      labels:
        run: nginx
    spec:
      containers:
      - name: <CONTAINER-NAME>
        image: nginx:latest
        ports:
        - containerPort: 80
        resources:
          limits:
            cpu: 500m
          requests:
            cpu: 200m
```

### Service
```yaml
apiVersion: v1
kind: Service
metadata:
  name: <service name>
  namespace: <namespace>
spec:
  selector:
    <key>: <value>
  ports:
  - port: 80
    targetPort: <application port>
    protocol: TCP
  type: NodePort
```

### Ingress
```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: <ingress name>
  namespace: <namespace>
  annotations:
    alb.ingress.kubernetes.io/load-balancer-name: <ALB name>
    alb.ingress.kubernetes.io/scheme: <internet-facing(public) or internal(private)>
    alb.ingress.kubernetes.io/subnets: <subnetid>, <subnetid>
    alb.ingress.kubernetes.io/target-type: ip
    alb.ingress.kubernetes.io/healthcheck-path: <>

spec:
  ingressClassName: alb
  rules:
  - http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: <service name>
            port:
              number: 80
```
