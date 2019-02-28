docker pull registry.cn-hangzhou.aliyuncs.com/google_containers/tiller:v2.8.2
docker tag registry.cn-hangzhou.aliyuncs.com/google_containers/tiller:v2.8.2 gcr.io/kubernetes-helm/tiller:v2.8.2

kubectl create serviceaccount --namespace kube-system tiller
kubectl create clusterrolebinding tiller-cluster-rule --clusterrole=cluster-admin --serviceaccount=kube-system:tiller

helm init --upgrade -i registry.cn-hangzhou.aliyuncs.com/google_containers/tiller:v2.8.2 --stable-repo-url https://kubernetes.oss-cn-hangzhou.aliyuncs.com/charts

kubectl patch deploy --namespace kube-system tiller-deploy -p '{"spec":{"template":{"spec":{"serviceAccount":"tiller"}}}}'      

# Not sure if need the following command
#kubectl create clusterrolebinding permissive-binding --clusterrole=cluster-admin --user=admin --user=kubelet --group=system:serviceaccounts;



