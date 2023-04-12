

## service account가져오기

kubectl get sa 

## service account 생성
kubectl create sa 계정명


# 특정 계정가져오기

kubectl get sa 계정명


## 서비스 어카운트 명령실행
kubectl get services --as system:serviceaccount:{네임스페이스}:{계정명}


## kubectl get role 
쿠버네티스 현재 네임스페이스에 대한 속하는 권한 출력


## kubectl get clusterrole
전역적이므로 클러스터 자체에 존재하는 모든 클러스터 롤의 목록을 출력 


kind: Role
metadata:
  namespace: default
  name: service-reader
rules:
- apiGroups: [""]
  resources: ["services"]
  verbs: ["get", "list"]


## Role를 부여했다고해서 서비스 어카운트에 롤이 적용되는게 하니다 . 권한

## 롤바인딩 해줘야한다. 

# 문제:
Grant this Service account access to list all PersistentVolumes in the cluster by creating an appropriate cluster role called pvviewer-role and ClusterRoleBinding called pvviewer-role-binding.

apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  name: service-reader-rolebinding
  namespace: default
subjects:
- kind: ServiceAccount    # 권한을 부여할 대상이 ServiceAccount
  name: ehdrms2034        # ynyoo이라는 이름의 서비스 어카운트에 권한을 부여
  namespace: default
roleRef:
  kind: Role              # Role에 정의된 권한을 부여
  name: service-reader    # service-role라는 이름의 Role을 대상에 연결
  apiGroup: rbac.authorization.k8s.io





# TIP
# yaml file 빠르게 만들기
kubectl run 이름 --image=redis --dry-run=client -o yaml


