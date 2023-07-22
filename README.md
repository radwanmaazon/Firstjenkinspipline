# Firstjenkinspipline
Deploy static coffee website by using jenkins pipeline and jenkins is applyed as a deployment on minikube but the website deployed on a slave which deployed as a deployment on minikube.

## To run my project on your host 
``` 
$   kubectl apply -f  jenkins/pv-jenkins.yml
$   kubectl apply -f  jenkins/namespace.yml
$   kubectl apply -f  jenkins/pvc-jenkins.yml
$   kubectl apply -f  jenkins/deploy-jenkins.yml
$   kubectl apply -f  jenkins/nodeport-jenkins.yml
$   kubectl apply -f  jenkins/jenkins-slave.yml
$   kubectl apply -f  jenkins/jenkins-slave-svc.yml
```
