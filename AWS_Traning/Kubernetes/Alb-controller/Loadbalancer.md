# Albcontroller를 생성하기전에
## Tag value는 1로 지정
```
kubernetes.io/role/elb
```
## Tag value는 1로 지정
```
kubernetes.io/role/elb
```

## OIDC 만들
```
eksctl utils associate-iam-oidc-provider --approve --cluster <클러스터 이름>
```

## 로드밸런서 역할 만들기
```
{
    "Version":"2012-10-17",
    "Statement":[
       {
          "Effect":"Allow",
          "Principal":{
             "Federated":"arn:aws:iam::<사용자 아이디>:oidc-provider/<OIDC URI>"
          },
          "Action":"sts:AssumeRoleWithWebIdentity",
          "Condition":{
             "StringEquals":{
                "<OIDC URI>:aud":"sts.amazonaws.com",
                "<OIDC URI>:sub":"system:serviceaccount:kube-system:aws-load-balancer-controller"
             }
          }
       }
    ]
 }
```
## IAM 정책역할
```
AdministratorAccess
```
```
ElasticLoadBalancingFullAccess
```

## service-account.yaml 다운로드
```
curl -o service-account.yaml https://raw.githubusercontent.com/wngnl05/Aws/main/Kubernetes/Alb_controller/service-account.yaml
```
```
kubectl apply -f service-account.yaml
```

## Helm 설치, 실행권한 부여
```
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3
chmod +x get_helm.sh
./get_helm.sh
helm repo add eks https://aws.github.io/eks-charts
helm repo update
```

## AWS Load Balancer Controller를 지정한 네임스페이스에 설치
```
helm install aws-load-balancer-controller eks/aws-load-balancer-controller \
  -n kube-system \
  --set clusterName=<클러스터 이름> \
  --set serviceAccount.create=false \
  --set serviceAccount.name=aws-load-balancer-controller
```

## AwsloadbalncerConrtroller 설치되었는지 확인하는 방법
```
kubectl get pods -n kube-system | grep aws-load-balancer-controller
```
```
helm list -n kube-system
```
```
kubectl get events -n kube-system | grep aws-load-balancer-controller
```

## Alb-controller를 삭제하는 방법
```
helm uninstall aws-load-balancer-controller -n kube-system
```
