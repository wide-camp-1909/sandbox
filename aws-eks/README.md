# Amazon Elastic Kubernetes Service

- **[eksctl](https://eksctl.io/)** - The official CLI for Amazonm EKS

## Create EKS cluster

### Helloworld
```bash
% eksctl create cluster --name sandbox --region ap-northeast-1 \
  --zones ap-northeast-1a,ap-northeast-1c --nodes 2 --nodes-min 2 --nodes-max 2 \
  --node-type t3.medium --node-zones ap-northeast-1a
```

## Helm install
```bash
% kubectl config get-contexts
% kubectl create serviceaccount tiller -n kube-system
% kubectl create clusterrolebinding tiller \
  --clusterrole cluster-admin --serviceaccount=kube-system:tiller
% helm init --service-account tiller --wait
```
