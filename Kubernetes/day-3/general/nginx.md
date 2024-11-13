 kubectl run nginx --image=nginx
pod/nginx created
lenovo@snj:~$ kubectl get pods
NAME         READY   STATUS              RESTARTS   AGE
nginx        0/1     ContainerCreating   0          20s
sample-pod   1/1     Running             0          163m
lenovo@snj:~$ kubectl describe pods nginx
Name:             nginx
Namespace:        default
Priority:         0
Service Account:  default
Node:             minikube/192.168.59.100
Start Time:       Wed, 13 Nov 2024 15:42:17 +0530
Labels:           run=nginx
Annotations:      <none>
Status:           Running
IP:               10.244.0.4
IPs:
  IP:  10.244.0.4
Containers:
  nginx:
    Container ID:   docker://8c3b128d911af8d39ddc721f1b1a5126ba067339e7d6913f67218fe30306bc49
    Image:          nginx
    Image ID:       docker-pullable://nginx@sha256:bc5eac5eafc581aeda3008b4b1f07ebba230de2f27d47767129a6a905c84f470
    Port:           <none>
    Host Port:      <none>
    State:          Running
      Started:      Wed, 13 Nov 2024 15:42:44 +0530
    Ready:          True
    Restart Count:  0
    Environment:    <none>
    Mounts:
      /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-njvzp (ro)
Conditions:
  Type                        Status
  PodReadyToStartContainers   True 
  Initialized                 True 
  Ready                       True 
  ContainersReady             True 
  PodScheduled                True 
Volumes:
  kube-api-access-njvzp:
    Type:                    Projected (a volume that contains injected data from multiple sources)
    TokenExpirationSeconds:  3607
    ConfigMapName:           kube-root-ca.crt
    ConfigMapOptional:       <nil>
    DownwardAPI:             true
QoS Class:                   BestEffort
Node-Selectors:              <none>
Tolerations:                 node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                             node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
Events:
  Type    Reason     Age   From               Message
  ----    ------     ----  ----               -------
  Normal  Scheduled  61s   default-scheduler  Successfully assigned default/nginx to minikube
  Normal  Pulling    60s   kubelet            Pulling image "nginx"
  Normal  Pulled     36s   kubelet            Successfully pulled image "nginx" in 24.255s (24.255s including waiting). Image size: 191670156 bytes.
  Normal  Created    34s   kubelet            Created container nginx
  Normal  Started    33s   kubelet            Started container nginx
lenovo@snj:~$ kubectl get pods -o wide
NAME         READY   STATUS    RESTARTS   AGE     IP           NODE       NOMINATED NODE   READINESS GATES
nginx        1/1     Running   0          3m18s   10.244.0.4   minikube   <none>           <none>
sample-pod   1/1     Running   0          166m    10.244.0.3   minikube   <none>           <none>
lenovo@snj:~$ 

