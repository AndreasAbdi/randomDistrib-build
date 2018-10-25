# Auto certing

This is for gce based kubernetes

## install nginx ingress

helm install --name nginx-ingress stable/nginx-ingress --set rbac.create=true

## install cert manager

helm-install --name my-release -f cert-manager-values.yaml cert-manager

### create the cert issuers

kubectl create -f ./letsencrypt-clusterissuer-staging.yaml
kubectl create -f ./letsencrypt-clusterissuer-prod.yaml

### Getting certs

Create your dns entries and configure to your nginx controller service's endpoint

For staging:

kubectl create -f ./backend-cert-staging.yaml
kubectl create -f ./frontend-cert-staging.yaml

For prod:

kubectl create -f ./backend-certificate-prod.yaml
kubectl create -f ./frontend-certificate-prod.yaml
