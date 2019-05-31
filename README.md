# k3s-demo

This repo contains materials used during k3s-demo on Nokia GarageTalks

## How to deploy k3s
curl -sfL https://get.k3s.io | sh –

## How to add agent:
curl -sfL https://get.k3s.io | K3S_URL=https://<IP_address>:6443 K3S_CLUSTER_SECRET="<secret>" sh -

## Deployment of Local Path Provisioner
kubectl apply -f https://raw.githubusercontent.com/rancher/local-path-provisioner/master/deploy/local-path-storage.yaml

## How to deploy kubernetes dashboard on k3s
kubectl create -f https://raw.githubusercontent.com/kubernetes/dashboard/master/aio/deploy/recommended/kubernetes-dashboard.yaml

kubectl proxy &

kubectl create serviceaccount dashboard -n default

kubectl create clusterrolebinding dashboard-admin -n default  --clusterrole=cluster-admin  --serviceaccount=default:dashboard

## How to get token to kubernetes dashboard
kubectl get secret $(kubectl get serviceaccount dashboard -o jsonpath="{.secrets[0].name}") -o jsonpath="{.data.token}" | base64 --decode
