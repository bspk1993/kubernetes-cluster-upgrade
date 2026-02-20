# kubernetes-cluster-upgrade
kubernetes cluster upgrade


1. First we have to upgrade from 1.25 to 1.26 version of the cluster

2. After it is successful we need to go to "ADD-ON:CoreDNS move the version from V1.93-eks build.2 to below versions of latest

3. After the "CORE DNS" upgrade go to the "kube proxy" which is in 1.25.6 version. so we need to change from 1.25.6 version to default i.e '1.26.2' version

4. After the 'kube-proxy' which need to go for the 'VPC-CNI'. So we need to change it from current version to default version and save changes

5. Go to 'COMPUTE' --> 'Node group' --> See  the 'AMI Release Version' --> Change Node Group which is in 1.25 prevous version to latest version --> wait for the Rolling update
   --> Go to Auto scaling see that 2 instances will go 4 instances --> Now we can see "1.26 version"

6. We have verify the resources & Check the Pod status in all whether they are running or not 
