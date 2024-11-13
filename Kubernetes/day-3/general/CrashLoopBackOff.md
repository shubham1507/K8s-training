# This error occure due to invalid image name in Objects/multi-pods.yaml

enovo@snj:~/kubtraining/Kubernetes/Objects$ ls
multi-pod.yaml  pod.yaml  service.yaml
lenovo@snj:~/kubtraining/Kubernetes/Objects$ kubectl create -f multi-pod.yaml
Warning: spec.containers[1].ports[0]: duplicate port definition with spec.containers[0].ports[0]
pod/multi-pod created
lenovo@snj:~/kubtraining/Kubernetes/Objects$ kubectl get pods
NAME         READY   STATUS     RESTARTS      AGE
multi-pod    1/2     NotReady   3 (45s ago)   69s
nginx        1/1     Running    0             11m
sample-pod   1/1     Running    0             174m
lenovo@snj:~/kubtraining/Kubernetes/Objects$ kubectl get pods
NAME         READY   STATUS             RESTARTS      AGE
multi-pod    1/2     CrashLoopBackOff   3 (26s ago)   81s
nginx        1/1     Running            0             11m
sample-pod   1/1     Running            0             174m
lenovo@snj:~/kubtraining/Kubernetes/Objects$ kubectl apply -f multi-pod.yaml
Warning: resource pods/multi-pod is missing the kubectl.kubernetes.io/last-applied-configuration annotation which is required by kubectl apply. kubectl apply should only be used on resources created declaratively by either kubectl create --save-config or kubectl apply. The missing annotation will be patched automatically.
The Pod "multi-pod" is invalid: spec: Forbidden: pod updates may not change fields other than `spec.containers[*].image`,`spec.initContainers[*].image`,`spec.activeDeadlineSeconds`,`spec.tolerations` (only additions to existing tolerations),`spec.terminationGracePeriodSeconds` (allow it to be set to 1 if it was previously negative)
  
lenovo@snj:~/kubtraining/Kubernetes/Objects$ kubectl get pods
NAME         READY   STATUS             RESTARTS      AGE
multi-pod    1/2     CrashLoopBackOff   4 (72s ago)   3m1s
nginx        1/1     Running            0             13m
sample-pod   1/1     Running            0             176m
lenovo@snj:~/kubtraining/Kubernetes/Objects$ kubectl logs multi-pod
Defaulted container "sample-pod" out of: sample-pod, sample-pod-busybox
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf


lenovo@snj:~/kubtraining/Kubernetes/Objects$ kubectl delete pod multi-pod
pod "multi-pod" deleted
lenovo@snj:~/kubtraining/Kubernetes/Objects$ kubectl delete pod nginx
pod "nginx" deleted
lenovo@snj:~/kubtraining/Kubernetes/Objects$ kubectl get pods
NAME         READY   STATUS    RESTARTS   AGE
sample-pod   1/1     Running   0          179m
lenovo@snj:~/kubtraining/Kubernetes/Objects$ ls
multi-pod.yaml  pod.yaml  service.yaml
lenovo@snj:~/kubtraining/Kubernetes/Objects$ kubectl delete -f pod.yaml  
Error from server (NotFound): error when deleting "pod.yaml": pods "nginx" not found
lenovo@snj:~/kubtraining/Kubernetes/Objects$ kubectl delete -f service.yaml  
error: error parsing service.yaml: error converting YAML to JSON: yaml: line 19: could not find expected ':'
lenovo@snj:~/kubtraining/Kubernetes/Objects$ 

