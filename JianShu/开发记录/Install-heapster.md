root@docker4:/home/cyang# helm install stable/heapster --name heapster --set rbac.create=true
NAME:   heapster
LAST DEPLOYED: Tue May 22 14:32:30 2018
NAMESPACE: default
STATUS: DEPLOYED

RESOURCES:
==> v1/ServiceAccount
NAME               SECRETS  AGE
heapster-heapster  1        1s

==> v1beta1/ClusterRoleBinding
NAME               AGE
heapster-heapster  1s

==> v1beta1/Role
NAME                         AGE
heapster-heapster-pod-nanny  1s

==> v1beta1/RoleBinding
NAME                         AGE
heapster-heapster-pod-nanny  1s

==> v1/Service
NAME      TYPE       CLUSTER-IP     EXTERNAL-IP  PORT(S)   AGE
heapster  ClusterIP  10.101.64.197  <none>       8082/TCP  1s

==> v1beta1/Deployment
NAME               DESIRED  CURRENT  UP-TO-DATE  AVAILABLE  AGE
heapster-heapster  1        0        0           0          1s

==> v1/Pod(related)
NAME                                READY  STATUS             RESTARTS  AGE
heapster-heapster-84595c87b5-fv8b2  0/2    ContainerCreating  0         1s


NOTES:
1. Get the application URL by running these commands:
  export POD_NAME=$(kubectl get pods --namespace default -l "app=heapster-heapster" -o jsonpath="{.items[0].metadata.name}")
  kubectl --namespace default port-forward $POD_NAME 8082
