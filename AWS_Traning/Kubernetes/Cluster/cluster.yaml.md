## Cluster Yaml
```yaml
apiVersion: eksctl.io/v1alpha5
kind: ClusterConfig
metadata:
  name: <클러스터 이름>
  region: <리전>
  version: "<쿠버네티스 버전>"
  
cloudWatch:
  clusterLogging:
    enableTypes:
    - "api"
    - "audit"
    - "authenticator"
    - "controllerManager"
    - "scheduler"
    
iam:
  withOIDC: true
vpc:
  id: <vpc 아이디>
  subnets:
    public:
      <리전>a-pub: { id: (서브넷 아이디) }
      <리전>b-pub: { id: (서브넷 아이디) }
    private:
      <리전>a-priv: { id: (서브넷 아이디) }
      <리전>b-priv: { id: (서브넷 아이디) }

managedNodeGroups:
  - name: <노드그룹 이름>
    instanceName: <인스턴스 이름>
    instanceType: <인스턴스 타입>
    minSize: <최소 노드 수>
    maxSize: <최대 노드 수>
    desiredCapacity: <생성할 노드 수>
    privateNetworking: true
    
    subnets:
      - <리전>a-priv
      - <리전>b-priv
      - <리전>a-pub
      - <리전>b-pub
    
    iam:
      withAddonPolicies:
        imageBuilder: true
        autoScaler: true
        awsLoadBalancerController: true
        cloudWatch: true
    labels:
      <key>: <value>
```
## 클러스터 생성
```
eksctl create cluster -f cluster.yaml
```
