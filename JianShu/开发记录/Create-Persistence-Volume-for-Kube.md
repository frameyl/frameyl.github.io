```
kubectl create -f <filename>.yaml
```
```
apiVersion: v1
kind: PersistentVolume
metadata:
  name: pv-nfs-ghostdb
spec:
  capacity:
    storage: 20Gi
  volumeMode: Filesystem
  accessModes:
    - ReadWriteOnce
  persistentVolumeReclaimPolicy: Recycle
  storageClassName: "ghostdb"
  mountOptions:
    - hard
    - nfsvers=4.1
  nfs:
    path: /mnt/ssd1/ghost-db
    server: docker9.ad.spirentcom.com
```
```
apiVersion: v1
kind: PersistentVolume
metadata:
  name: pv-nfs-ghost
spec:
  capacity:
    storage: 20Gi
  volumeMode: Filesystem
  accessModes:
    - ReadWriteOnce
  persistentVolumeReclaimPolicy: Recycle
  storageClassName: "ghost"
  mountOptions:
    - hard
    - nfsvers=4.1
  nfs:
    path: /mnt/ssd1/ghost
    server: 10.61.36.27
```
