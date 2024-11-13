sudo docker login
Authenticating with existing credentials...
WARNING! Your password will be stored unencrypted in /root/.docker/config.json.
Configure a credential helper to remove this warning. See
https://docs.docker.com/engine/reference/commandline/login/#credentials-store

Login Succeeded
lenovo@snj:~$ code pod.yaml
lenovo@snj:~$ kubectl create -f pod.yaml
pod/sample-pod created
lenovo@snj:~$ kubectl get nodes
NAME       STATUS   ROLES           AGE   VERSION
minikube   Ready    control-plane   11m   v1.31.0
lenovo@snj:~$ kubectl get pods
NAME         READY   STATUS              RESTARTS   AGE
sample-pod   0/1     ContainerCreating   0          16s
lenovo@snj:~$ kubectl get pods
NAME         READY   STATUS    RESTARTS   AGE
sample-pod   1/1     Running   0          65m
lenovo@snj:~$ ls
Desktop    Downloads  kubtraining  main.pdf  Pictures  Public  Templates
Documents  ITC.py     latexcv      Music     pod.yaml  snap    Videos
lenovo@snj:~$ code service.yaml
lenovo@snj:~$ kubectl create -f service.yaml  
service/sample-service created
lenovo@snj:~$ kubectl get svc
NAME             TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)        AGE
kubernetes       ClusterIP   10.96.0.1       <none>        443/TCP        162m
sample-service   NodePort    10.101.37.224   <none>        80:32123/TCP   3m2s
lenovo@snj:~$ kubectl get pods
NAME         READY   STATUS    RESTARTS   AGE
sample-pod   1/1     Running   0          152m
lenovo@snj:~$ cd kubtraining/ 
lenovo@snj:~/kubtraining$ 