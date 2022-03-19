# 1.1 How to build the docker image

```
docker build . -t anirav32/movella
```
# 1.2 Push the docker image to remote docker hub

```
docker push anirav32/movella
``` 
# 1.3 install minikube 

```
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```
# 1.4 start  minikube cluster
```
minikube start
```
# 1.5 Deploy application
```
cd kube
minikube kubectl -- create -f deployment.yaml

minikube kubectl -- create -f service.yaml
```
## minikube output 
1. I have used NodePort service in minikube to expose the application.

```
developer@ip-172-31-43-109:~/kube$ minikube kubectl get deploy
NAME             READY   UP-TO-DATE   AVAILABLE   AGE
abs-deployment   1/1     1            1           20m
developer@ip-172-31-43-109:~/kube$ minikube kubectl get po
NAME                              READY   STATUS    RESTARTS   AGE
abs-deployment-7f4fd5889b-j6k8w   1/1     Running   0          20m
developer@ip-172-31-43-109:~/kube$ minikube kubectl get svc
NAME          TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)        AGE
abs-service   NodePort    10.102.124.175   <none>        80:30007/TCP   18m
kubernetes    ClusterIP   10.96.0.1        <none>        443/TCP        28m
developer@ip-172-31-43-109:~/kube$

```
