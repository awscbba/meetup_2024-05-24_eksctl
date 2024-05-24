# meetup_2024-05-24_eksctl

## Create EKS cluster from file
eksctl create cluster -f cluster.yaml

## Drop EKS cluster from file
eksctl delete cluster -f cluster.yaml

## Create EKS cluster in console
eksctl create cluster --name=dev-cluster --version=1.29 --auto-kubeconfig --node-type=t2.micro --nodes=1 
eksctl create cluster --name=dev-cluster --version=1.29 --auto-kubeconfig --node-type=t2.micro --nodes-min=1 --nodes-max=3

## Get EKS config
eksctl get cluster dev-cluster-01 --region=us-east-1


## Get EKS node group 
eksctl get nodegroup --cluster=dev-cluster-01

## Scale EKS Cluster
eksctl scale nodegroup --cluster=dev-cluster-01 --region us-east-1 --nodes=2 ng-workers 


## Deploy Apache with PHP in EKS
kubectl apply -f deployment/php-apache-namespace.yaml
kubectl get ns

kubectl apply -f deployment/php-apache-deployment.yaml
kubectl get po -n demo

kubectl apply -f deployment/php-apache-hpa.yaml
kubectl get hpa -n demo

kubectl apply -f deployment/php-apache-loadbalancer.yaml
kubectl get svc -n demo
