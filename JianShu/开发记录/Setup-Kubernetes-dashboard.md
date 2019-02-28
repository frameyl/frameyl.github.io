## Setup the service
```
docker pull registry.cn-hangzhou.aliyuncs.com/google_containers/kubernetes-dashboard-amd64:v1.8.3
docker tag registry.cn-hangzhou.aliyuncs.com/google_containers/kubernetes-dashboard-amd64:v1.8.3 k8s.gcr.io/kubernetes-dashboard-amd64:v1.8.3

git clone https://github.com/kubernetes/dashboard
kubectl apply -f  ./src/deploy/recommended/kubernetes-dashboard.yaml
```

## Make the service accessible
```
kubectl -n kube-system edit svc/kubernetes-dashboard
```
Change .spec.type to NodePort. And then use `kubectl -n kube-system get svc/kubernetes-dashboard`
to get the external port number of dashboard. Then use https://<Kube Master IP>:<port>/ to access the dashboard.

## Create Token for cluster admin
use kubectl apply -f to apply the following config
```
kind: ClusterRoleBinding
apiVersion: rbac.authorization.k8s.io/v1beta1
metadata:
  name: admin
  annotations:
    rbac.authorization.kubernetes.io/autoupdate: "true"
roleRef:
  kind: ClusterRole
  name: cluster-admin
  apiGroup: rbac.authorization.k8s.io
subjects:
- kind: ServiceAccount
  name: admin
  namespace: kube-system
---
apiVersion: v1
kind: ServiceAccount
metadata:
  name: admin
  namespace: kube-system
  labels:
    kubernetes.io/cluster-service: "true"
    addonmanager.kubernetes.io/mode: Reconcile
```

## Get Tokens for cluster admin
```
kubectl -n kube-system get secret|grep admin-token
kubectl -n kube-system get secret admin-token-<your id> -o jsonpath={.data.token}|base64 -d
```

## Get Tokens for default namespace
```
kubectl create rolebinding default-admin --clusterrole=admin --serviceaccount=default:default --namespace=default
kubectl get secret | grep default-token
kubectl get secret default-token-<your id> -o jsonpath={.data.token}|base64 -d
```

## Reference
https://blog.qikqiak.com/post/update-kubernetes-dashboard-more-secure/
https://jimmysong.io/kubernetes-handbook/guide/auth-with-kubeconfig-or-token.html
