## Hello world
```bash
% eksctl create cluster --name sandbox --region ap-northeast-1 \
--zones ap-northeast-1a,ap-northeast-1c --nodes 2 --nodes-min 2 --nodes-max 2 \
--node-type t3.medium --node-zones ap-northeast-1a
```
```txt
[ℹ]  using region ap-northeast-1
[ℹ]  subnets for ap-northeast-1a - public:192.168.0.0/19 private:192.168.64.0/19
[ℹ]  subnets for ap-northeast-1c - public:192.168.32.0/19 private:192.168.96.0/19
[ℹ]  nodegroup "ng-e5b81515" will use "ami-0a67c71d2ab43d36f" [AmazonLinux2/1.13]
[ℹ]  using Kubernetes version 1.13
[ℹ]  creating EKS cluster "sandbox" in "ap-northeast-1" region
[ℹ]  will create 2 separate CloudFormation stacks for cluster itself and the initial nodegroup
[ℹ]  if you encounter any issues, check CloudFormation console or try 'eksctl utils describe-stacks --region=ap-northeast-1 --name=sandbox'
[ℹ]  CloudWatch logging will not be enabled for cluster "sandbox" in "ap-northeast-1"
[ℹ]  you can enable it with 'eksctl utils update-cluster-logging --region=ap-northeast-1 --name=sandbox'
[ℹ]  2 sequential tasks: { create cluster control plane "sandbox", create nodegroup "ng-e5b81515" }
[ℹ]  building cluster stack "eksctl-sandbox-cluster"
[ℹ]  deploying stack "eksctl-sandbox-cluster"
```
