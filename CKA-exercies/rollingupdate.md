
# 

### 문제

Create a new deployment called nginx-deploy, with image nginx:1.16 and 1 replica. Record the version. Next upgrade the deployment to version 1.17 using rolling update. Make sure that the version upgrade is recorded in the resource annotation.

kubectl create deployment nginx-deploy  --image=nginx:1.16 --replicas=1


## --record 해줘야 히스토리에 남는다 
kubectl set image deployment/nginx-deploy nginx=nginx:1.17 --record



## 변경 했는지 체크
kubectl rollout status deployment


