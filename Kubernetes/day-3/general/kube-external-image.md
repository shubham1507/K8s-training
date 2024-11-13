lenovo@snj:~/kubtraining/Kubernetes/Objects$ kubectl run node-hello-pod --image 839024/node-hello-world:latest --port=80
pod/node-hello-pod created

lenovo@snj:~/kubtraining/Kubernetes/Objects$ kubectl get pods
NAME             READY   STATUS              RESTARTS   AGE
node-hello-pod   0/1     ContainerCreating   0          24s
redis            0/1     ImagePullBackOff    0          18m
sample-pod       1/1     Running             0          3h26m
lenovo@snj:~/kubtraining/Kubernetes/Objects$ 
