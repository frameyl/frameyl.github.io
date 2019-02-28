The initial token of joining K8S cluster will expire for a couple of days. After that, you will need to generate the new token again. Please follow the below steps to have your new line of node join.
```
# login to master node
# create a new bootstrap token
$ kubeadm token create
abcdef.1234567890abcdef

# get root ca cert fingerprint
$ openssl x509 -pubkey -in /etc/kubernetes/pki/ca.crt | openssl rsa -pubin -outform der 2>/dev/null | openssl dgst -sha256 -hex | sed 's/^.* //'
e18105ef24bacebb23d694dad491e8ef1c2ea9ade944e784b1f03a15a0d5ecea 

# login to the new worker node
# join to cluster 
$ kubeadm join --token abcdef.1234567890abcdef --discovery-token-ca-cert-hash sha256:e18105ef24bacebb23d694dad491e8ef1c2ea9ade944e784b1f03a15a0d5ecea 1.2.3.4:6443
```
