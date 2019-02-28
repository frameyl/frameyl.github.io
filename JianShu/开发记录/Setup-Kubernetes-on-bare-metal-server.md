## 安装kubelet，kubeadm，kubectl
#####Option 1:  下载binary
```
apt-get install -ydd curl
curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl
chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin/kubectl
```

```
wget https://github.com/coreos/etcd/releases/download/v3.2.19/etcd-v3.2.19-linux-amd64.tar.gz
wget https://github.com/kubernetes/kubernetes/releases/download/$(curl -sSL https://dl.k8s.io/release/stable.txt)/kubernetes.tar.gz
```

```
tar xf kubernetes.tar.gz
./cluster/get-kube-binaries.sh
cd server
tar xf kubernetes-server-linux-amd64.tar.gz
cd kubernetes/server/bin
chmod +x {kubeadm,kubelet,kubectl}
cp * /usr/local/bin
curl -sSL "https://raw.githubusercontent.com/kubernetes/kubernetes//build/debs/kubelet.service" | sed "s:/usr/local/bin:/opt/bin:g" > /etc/systemd/system/kubelet.service
mkdir -p /etc/systemd/system/kubelet.service.d
curl -sSL "https://raw.githubusercontent.com/kubernetes/kubernetes//build/debs/10-kubeadm.conf" | sed "s:/usr/local/bin:/opt/bin:g" > /etc/systemd/system/kubelet.service.d/10-kubeadm.conf
```

#####Option 2: 使用阿里云镜像Repo
```
curl -s https://mirrors.aliyun.com/kubernetes/apt/doc/apt-key.gpg | apt-key add -
cat <<EOF >/etc/apt/sources.list.d/kubernetes.list
deb https://mirrors.aliyun.com/kubernetes/apt/ kubernetes-xenial main
EOF

apt-get update
#apt-get install -y kubelet kubeadm kubectl
apt-get install kubeadm=1.9.2-00 kubectl=1.9.2-00 kubelet=1.9.2-00
```

## 在Master上安装容器
执行如下脚本
```
root@docker4:/home/cyang# cat dockers_k8s.1.9.2.sh
#!/bin/bash
KUBE_VERSION=v1.9.2
KUBE_PAUSE_VERSION=3.0
ETCD_VERSION=3.1.11
DNS_VERSION=1.14.7

GCR_URL=gcr.io/google_containers
ALIYUN_URL=registry.cn-hangzhou.aliyuncs.com/google_containers

images=(kube-proxy-amd64:${KUBE_VERSION}
kube-scheduler-amd64:${KUBE_VERSION}
kube-controller-manager-amd64:${KUBE_VERSION}
kube-apiserver-amd64:${KUBE_VERSION}
pause-amd64:${KUBE_PAUSE_VERSION}
etcd-amd64:${ETCD_VERSION}
k8s-dns-sidecar-amd64:${DNS_VERSION}
k8s-dns-kube-dns-amd64:${DNS_VERSION}
k8s-dns-dnsmasq-nanny-amd64:${DNS_VERSION})

for imageName in ${images[@]} ; do
  docker pull $ALIYUN_URL/$imageName
  docker tag $ALIYUN_URL/$imageName $GCR_URL/$imageName
done
```

## 初始化Kubernetes Master
创建配置文件
```
root@docker4:/home/cyang# cat kubernetes_init/kubeadm.conf
apiVersion: kubeadm.k8s.io/v1alpha1
kind: MasterConfiguration
api:
  advertiseAddress: 0.0.0.0
networking:
  podSubnet: 10.244.0.0/16
etcd:
  image: registry.cn-hangzhou.aliyuncs.com/google_containers/etcd-amd64:3.1.11
kubernetesVersion: v1.9.2
imageRepository: registry.cn-hangzhou.aliyuncs.com/google_containers
```
初始化Kube
```
kubeadm init --config ./kubernetes_init/kubeadm.conf
```
保存下面一行
> kubeadm join --token a1deaa.8b2881f4ab2fe627 10.65.116.102:6443 --discovery-token-ca-cert-hash sha256:9324252af7cbbc799c96926b97bc83a506285bbb26c894fff58833bd5401ad22

安装kubectl配置文件
```
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
```
## 安装网络组件
```
docker pull registry.cn-beijing.aliyuncs.com/k8s_images/flannel:v0.9.1-amd64
docker tag registry.cn-beijing.aliyuncs.com/k8s_images/flannel:v0.9.1-amd64 quay.io/coreos/flannel:v0.9.1-amd64
kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/v0.9.1/Documentation/kube-flannel.yml
```

## 初始化Node节点
```
#!/bin/bash
KUBE_VERSION=v1.9.2
KUBE_PAUSE_VERSION=3.0
ETCD_VERSION=3.1.11
DNS_VERSION=1.14.7

GCR_URL=gcr.io/google_containers
ALIYUN_URL=registry.cn-hangzhou.aliyuncs.com/google_containers

images=(kube-proxy-amd64:${KUBE_VERSION}
pause-amd64:${KUBE_PAUSE_VERSION}
)

for imageName in ${images[@]} ; do
  docker pull $ALIYUN_URL/$imageName
  docker tag $ALIYUN_URL/$imageName $GCR_URL/$imageName
done

docker pull registry.cn-beijing.aliyuncs.com/k8s_images/flannel:v0.9.1-amd64
docker tag registry.cn-beijing.aliyuncs.com/k8s_images/flannel:v0.9.1-amd64 quay.io/coreos/flannel:v0.9.1-amd64
```
执行上面master获取的一行
```
kubeadm join --token 140a5c.9a35e667017bcf81 docker4:6443 --discovery-token-ca-cert-hash sha256:b11146d1c0db78c587ed7ebe5e26483186abac6cf7c771ce5b689b37879665c3
```
