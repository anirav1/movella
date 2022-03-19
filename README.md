# 1.1 How to build the docker image

```
docker build . -t anirav32/movella  #change the docker image tag as your remote dockerhub repo name
```
# 1.2 Push the docker image to remote docker hub

```
docker push anirav32/movella  # login with your  docker hub  credetials 
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
1) I have used the public availble docker image, so no need to add the docker credentials, if your using the private docker image, you need to create kubernetes secret and use that secret in deployment file like flollowing link https://kubernetes.io/docs/tasks/configure-pod-container/pull-image-private-registry/

2) I have used the NodePort type service, so we can browse the application with machineip:nodeport

```
cd kube
minikube kubectl -- create -f deployment.yaml

minikube kubectl -- create -f service.yaml
```
## kubernetes  output 

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
