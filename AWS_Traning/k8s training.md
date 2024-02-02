### kubectl install command

```
sudo chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin
```

### cluster yaml

```
apiVersion: eksctl.io/v1alpha5
kind: ClusterConfig
metadata:
  name: <cluster name>
  region: <region>
  version: "<kubectl version>"
  
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
  id: <vpc id>
  subnets:
    public:
      <region>a-pub: { id: (subnet-id) }
      <region>b-pub: { id: (subnet-id) }
    private:
      <region>a-priv: { id: (subnet-id) }
      <region>b-priv: { id: (subnet-id) }

managedNodeGroups:
  - name: <Nodegroup name>
    instanceName: <Name>
    instanceType: <Type>
    minSize: <min>
    maxSize: <max>
    desiredCapacity: <make Number>
    privateNetworking: true
    
    subnets:
      - <region>a-priv
      - <region>b-priv
      - <region>a-pub
      - <region>b-pub
    
    iam:
      withAddonPolicies:
        imageBuilder: true
        autoScaler: true
        awsLoadBalancerController: true
        cloudWatch: true
    labels:
      <key>: <value>
```

### cluster create command

```
eksctl create cluster -f cluster.yaml
```

### cluster remove command

```
eksctl delete cluster -f cluster.yaml
```
