# Kubernetes

## Architechture
[Kubernetes Architechture Intro Notes](https://projects.100xdevs.com/tracks/kubernetes-1/Kubernetes-Part-1-1)

### Starting first kubernetes cluster locally

```
➜ brew install kind
```
```
➜ brew install kubectl
```
- Cluster Config for 1 master node and 2 worker nodes:

```
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
- role: control-plane
- role: worker
- role: worker
```
```
➜ kind create cluster --config clusters.yml --name local
```
```
➜ docker ps
CONTAINER ID   IMAGE                      COMMAND                  CREATED              STATUS              PORTS                                            NAMES
eb928ef5e8dd   kindest/node:v1.32.2       "/usr/local/bin/entr…"   About a minute ago   Up About a minute   127.0.0.1:63413->6443/tcp                        local-control-plane
43ecfe3d0a64   kindest/node:v1.32.2       "/usr/local/bin/entr…"   About a minute ago   Up About a minute                                                    local-worker
8f5755a0b804   kindest/node:v1.32.2       "/usr/local/bin/entr…"   About a minute ago   Up About a minute                                                    local-worker2

```
## Cluster Credentials
```
➜ cat ~/.kube/config
```
```
➜ kubectl get pods
No resources found in default namespace.
```

## Starting first pod using k8s
```
➜  kubectl run nginx --image=nginx --port=80
pod/nginx created
```
```
➜ kubectl get pods
NAME    READY   STATUS    RESTARTS   AGE
nginx   1/1     Running   0          52s
```
```
➜ kubectl describe pods nginx
```
```
➜ kubectl delete pods nginx
```

## Manifest File
```
➜ kubectl apply -f manifest.yml
pod/nginx created
```
```
➜ kubectl get pods
NAME    READY   STATUS    RESTARTS   AGE
nginx   1/1     Running   0          41s
```