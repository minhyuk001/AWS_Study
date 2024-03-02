## Subnet tag - ( Value : 1 )
### Public
```
kubernetes.io/role/elb
```

### Private
```
kubernetes.io/role/internal-elb
```

=======================================================================================

### IAM install
```
curl -o loadbalancer_role.yaml https://raw.githubusercontent.com/wngnl05/Aws/main/Kubernetes/Alb_controller/loadbalancer_role.yaml
```

### IAM Role Add
```
AdministratorAccess
```
```
ElasticLoadBalancingFullAccess
```

### service-account install - ( ARN Edit )
```
curl -o service-account.yaml  https://raw.githubusercontent.com/wngnl05/Aws/main/Kubernetes/Alb_controller/service-account.yaml
```
```
kubectl apply -f service-account.yaml
```

### Helm install
```
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3
chmod +x get_helm.sh
./get_helm.sh
helm repo add eks https://aws.github.io/eks-charts
helm repo update
```

### loadbalancer controller install
```
helm install aws-load-balancer-controller eks/aws-load-balancer-controller \
  -n kube-system \
  --set clusterName=<클러스터 이름> \
  --set serviceAccount.create=false \
  --set serviceAccount.name=aws-load-balancer-controller
```
