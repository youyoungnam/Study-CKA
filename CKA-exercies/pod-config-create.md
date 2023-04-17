

## 문제
Create the directory named manifests. Within the directory, create two files: pod.yaml and configmap.yaml. The pod.yaml file should define a Pod named nginx with the image nginx:1.21.1. The configmap.yaml file defines a ConfigMap named logs-config with the key-value pair dir=/etc/logs/traffic.log. Create both objects with a single, declarative command.


pod 생성
kubectl run nginx --image=nginx:1.21.1 -o yaml --dry-run=client > pod.yaml


Config.yaml 작성
```
apiVersion: v1
kind: ConfigMap
metadata:
  name: logs-config
data:
  dir: /etc/logs/traffic.log
```

kubectl apply -f 폴더이름 -R

kubectl apply -f manifests -R
