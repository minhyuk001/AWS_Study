```
kubectl apply -f <filename>
```

### Resource Info Get
```
kubectl get <resource> -n <namespace>
```

### Deployment
```yaml
apiVersion: apps/v1
kind: Deployment

metadata:
  name: <deployment 이름>
  namespace: <namespace 이름>
  labels:
    <key> : <value>  
    
spec:
  replicas: <생성할 파드 수>
  selector:
    matchLabels:
      <key> : <value>
      
  template:
    metadata:
      labels:
        <key> : <value>
        
    spec:
      nodeSelector:
        <Node key>: <Node Value>

      containers:
      - name: <컨테이너 이름>
        image: <Docekr 이미지 경로>
        ports:
        - containerPort: <애플리케이션 포트>

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
