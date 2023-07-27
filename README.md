# Firstjenkinspipline
Deploy static coffee website by using jenkins pipeline and jenkins is applyed as a deployment on minikube but the website deployed on a slave which deployed as a deployment on minikube.

## To run my project on your host 
``` sh
$   kubectl apply -f  jenkins/pv-jenkins.yml
$   kubectl apply -f  jenkins/namespace.yml
$   kubectl apply -f  jenkins/pvc-jenkins.yml
$   kubectl apply -f  jenkins/deploy-jenkins.yml
$   kubectl apply -f  jenkins/nodeport-jenkins.yml
$   kubectl apply -f  jenkins/jenkins-slave.yml
$   kubectl apply -f  jenkins/jenkins-slave-svc.yml
```
You may have some issuse when deploying jenkins as deployment on minikube and make an init container to install docker and kubectl and mount them on jenkins pod. You can work around this problem by give dockerfile full permissions and deploy.
``` sh
$  chmod 777 /var/run/docker.sock 
```
configure slave to deploy website on it 
## Deploying website by slave which deploying on minikube and IP for minikube 192.168.49.2 and port for slave service 30101
# 1- 
![image](https://github.com/redwan2050/Firstjenkinspipline/blob/master/images/website-1.png)
# 2- 
![image](https://github.com/redwan2050/Firstjenkinspipline/blob/master/images/website-2.png)
## deploying jenkins on minikube and access it by nodeport service 192.168.49.2:30100
# 1- 
![image](https://github.com/redwan2050/Firstjenkinspipline/blob/master/images/jenkins.png)
# 2- 
![image](https://github.com/redwan2050/Firstjenkinspipline/blob/master/images/jenkins-master.png)
# 3- 
![image](https://github.com/redwan2050/Firstjenkinspipline/blob/master/images/branches.png)
## Ownership
![Radwan Maazon](images/Radwan1.jpg)|
|:-----------------:|
|[Radwan Maazon](https://github.com/redwan2050)|




