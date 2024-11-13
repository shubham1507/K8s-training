kubectl create -f redis.yaml 
pod/redis created
lenovo@snj:~/kubtraining/Kubernetes/Objects$ kubectl get pods 
NAME         READY   STATUS         RESTARTS   AGE
redis        0/1     ErrImagePull   0          36s
sample-pod   1/1     Running        0          3h9m
lenovo@snj:~/kubtraining/Kubernetes/Objects$ kubectl get pods --watch
NAME         READY   STATUS             RESTARTS   AGE
redis        0/1     ImagePullBackOff   0          47s
sample-pod   1/1     Running            0          3h9m

