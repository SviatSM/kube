# Google Cloud Platform - Kubernetes

This is simple project which will describle how to use Kubernetes in Google Cloud Platform.

# Before begin

  - register your google cloud account;
  - enable Kubernetes Engine API, Container Registry API;
  - enable for your vm instance access to Cloud APIs;
  - install Cloud SDK -[Instruction](https://cloud.google.com/sdk/docs/#rpm).

# Creating Kubernetes cluster

 In Kubernetes engine service create cluster.
 
 ![1](images/1.png)
 
 
# Kubernetes dashboard

  - connect to your cluster via Google SDK;
  
 ![2](images/2.png)
 
  - creating clusterrole:
 
  ```bash
  kubectl create clusterrolebinding kubernetes-dashboard -n kube-system --clusterrole=cluster-admin --serviceaccount=kube-  system:kubernetes-dashboard
  ```
  - apply recommended kubernetes dashboard:
  
  ```bash
  kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v1.10.1/src/deploy/recommended/kubernetes-dashboard.yaml
  ```
  - get token:
  ```bash
  kubectl -n kube-system describe secrets kubernetes-dashboard-token
  ```
  
  - start kubernetes dashboard:
  
  ```bash
  kubectl proxy
  ```
  
  - open dashboard:
  
  ```bash
  http://localhost:8001/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/
```

 # Kubernetes cluster
 
  ```bash
  [root@gcloud ~]# gcloud container clusters get-credentials cluster1 --zone us-central1-a ***************
                   Fetching cluster endpoint and auth data.
                   kubeconfig entry generated for cluster1.
 ```
 
 ```bash
 [root@gcloud ~]# kubectl get nodes
NAME                                      STATUS   ROLES    AGE     VERSION
gke-cluster1-default-pool-64807803-kwbt   Ready    <none>   2d19h   v1.12.7-gke.10
gke-cluster1-default-pool-64807803-zm7b   Ready    <none>   2d19h   v1.12.7-gke.10
```

```bash
[root@gcloud ~]# kubectl get pods
NAME                          READY   STATUS    RESTARTS   AGE
gameoflife-64fd98b559-hltgf   1/1     Running   0          2d
```

![3](images/3.png)


![4](images/4.png)


# Deploying

