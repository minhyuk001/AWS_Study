```yml
version: 0.0

Resources:
  - TargetService:
      Type: AWS::ECS::Service
      Properties:
        TaskDefinition: "<TASK_DEFINITION>" # 수정 안함
        LoadBalancerInfo:
          ContainerName: "<TaskDef 컨테이너 이름>"
          ContainerPort: <컨테이너 포트>
```
