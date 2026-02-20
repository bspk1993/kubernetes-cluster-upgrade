# kubernetes-cluster-upgrade
kubernetes cluster upgrade


1. First we have to upgrade from 1.25 to 1.26 version of the cluster

2. After it is successful we need to go to "ADD-ON:CoreDNS move the version from V1.93-eks build.2 to below versions of latest

3. After the "CORE DNS" upgrade go to the "kube proxy" which is in 1.25.6 version. so we need to change from 1.25.6 version to default i.e '1.26.2' version

4. After the 'kube-proxy' which need to go for the 'VPC-CNI'. So we need to change it from current version to default version and save changes

5. Go to 'COMPUTE' --> 'Node group' --> See  the 'AMI Release Version' --> Change Node Group which is in 1.25 prevous version to latest version --> wait for the Rolling update
   --> Go to Auto scaling see that 2 instances will go 4 instances --> Now we can see "1.26 version"

6. We have verify the resources & Check the Pod status in all whether they are running or not



**# Commands For AWS EKS** 

---> aws eks create-cluster --name my-cluster --kubernetes-version1.28 --role
---> aws eks describe-cluster --name mycluster
---> aws eks delete-cluster --name mycluster

NODE GROUP MANAGEMENT

---> aws eks create -node group --cluster-name mycluster --nodegroupname my-nodegroup --scaling-config minsize=1, maxsize=3 desired size=2 --instance-type t3.medium --amitype AL2_*86_64
---> aws eks describe --nodegroup --cluster-name mycluster --nodegroup-name my-node group
---> aws eks delete -nodegroup --cluster-name mycluster --nodegroup-name my-node group

ADD-ON MANAGEMENT

--> aws eks create -addon --cluster-name mycluster --addon-name VPC-CNI
--> aws eks describe -addon --cluster-name mycluster --addon-name VPC-CNI
--> aws eks update-addon --cluster-name mycluster --addon -name VPC-CNI --addon-version V1.11.4-eksbuild.1

**eksctl for EKS **
**cluster creation**

eksctl create cluster --name mycluster --region us-west-2 --version 1.28 --nodegroup-name standard-workers --node-type t3.medium --nodes3

**cluster deletion**

eksctl delete cluster --name mycluster --region us-west-2

**Nodegroup management**

eksctl create node-group --cluster mycluster --name my-new-nodegroup --node-type m5.large --nodes 2

**Kubectl for kubernetes**

kubectl is the standard kubernetes command-line tool

kubectl apply -f my-deployment.yaml
kubectl describe service my-service 
kubectl log my-pod

**Cluster information**

kubectl get nodes
kubectl get namespaces
kubectl cluster-info



