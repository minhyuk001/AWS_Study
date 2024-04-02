```yml
version: 0.2
phases:
  pre_build:
    commands:
      - DOCKER_IMAGE=<URL>:<TAG>
  build:
    commands:
      # Docker Build & Push
  post_build:
    commands:
      - sed -i "s#<WNGNL_IMAGE>#$DOCKER_IMAGE#g" taskdef.json
      
artifacts:
  files:
    - 'appspec.yml'
    - 'taskdef.json'
```
