### kubectl install command

```
sudo chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin
```

### aws kubectl install web
```
https://docs.aws.amazon.com/eks/latest/userguide/install-kubectl.html
```

### aws eksctl install web
```
https://docs.aws.amazon.com/emr/latest/EMR-on-EKS-DevelopmentGuide/setting-up-eksctl.html
```

### kubectl file apply
```
kubectl apply -f <filename>
```

### Resource Info Get
```
kubectl get <resource> -n <namespace>
```

### Status Check
```
curl <alb-dns>/health
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
  name: <서비스 이름>
  namespace: <네임스페이스 이름>
spec:
  selector:
    <key>: <value>
  ports:
  - port: 80
    targetPort: <애플리케이션 포트>
    protocol: TCP
  type: NodePort
```

### Ingress
```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: <ingress 이름>
  namespace: <네임스페이스 이름>
  annotations:
    alb.ingress.kubernetes.io/load-balancer-name: <ALB 이름>
    alb.ingress.kubernetes.io/scheme: <> //internet-facing(Public), internal(Private)
    alb.ingress.kubernetes.io/subnets: <서브넷 아이디>, <서브넷 아이디>
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
            name: <서비스 이름>
            port:
              number: 80
```
