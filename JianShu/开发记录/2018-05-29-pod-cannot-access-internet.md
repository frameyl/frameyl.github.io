https://blog.yaakov.online/kubernetes-getting-pods-to-talk-to-the-internet/

```
apiVersion: v1
kind: ConfigMap
metadata:
  name: kube-dns
  namespace: kube-system
data:
  upstreamNameservers: |
    ["10.65.50.20"]
```

restart kube-dns pod.
