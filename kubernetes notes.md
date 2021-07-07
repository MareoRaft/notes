Kubernetes
==========
Idea: With kubernetes you (1) create a cluster of nodes and then (2) deploy deployments on it.

k8s - short for kubernetes
k8s - a CLI
k9s - stripped down version of k8s
AWS eks - AWS elastic kubernetes service (here "elastic" just means that the size adjusts to your needs)


## currently learning on:
https://kubernetes.io/docs/tutorials/kubernetes-basics/deploy-app/deploy-intro/




## great video:
https://vimeo.com/245778144/4d1d597c5e

## key terms:
pod - "meta container". (containers typically different) Could contain single docker container, or a few that need to work together. For example, an app in one container, and a sibling app that collects performance metrics in another, all together in one pod.
deployment - "meta pod". (pods typically identical) multiple pods running with load balancing and fault tolerance
namespace - contains deployment, replica-set, serviceaccount, secret, nodes
service - port forwarder and load balancer to the pods
ingress - point hostname to service IP address



minikube start  -  start your 1-node cluster
minikube dashboard  -  see dashboard
kubectl get po -A  -  see all running pods (po == pod == pods)

kubectl create deployment hello-minikube --image=k8s.gcr.io/echoserver:1.4
kubectl expose deployment hello-minikube --type=NodePort --port=8080

kubectl get services hello-minikube

kubectl create namespace <name>
kubectl create -f resource.yaml  ->  to create more complicated things, specify in a yaml

# more kubectl commands
kubectl cluster-info
kubectl get events,nodes,pods,deployment,service,ingress


## resouce.yaml example
apiVersion: apps/v1beta2
kind: Deployment
...

# demo (example of setting up project)
## setup
kubectl config set-cluster <cluster> --server=<url> --certificate-authority=./ca.crt --embed-certs=true
kubectl config set-credentials <user> --token=<token>
kubectl config use-context <context>  # kindof like a namespace for your current work
## create resources
kubectl create namespace <name>  # namespace for project
kubectl --namespace=<name> create -f deployment.yaml  # create deployment (and pods)
kubectl --namespace=<name> create -f service.yaml  # create service (to expose pods)
kubectl create -f ingress.yaml  # route hostname to service via ingress
## create resources MORE EASILY
kubectl apply <dirpath>  # create/update all things specified by yaml files in dir
## check on what you made
kubectl get pods,deployment,service,ingress
## SUPER command to do it all automatically??



# kubernetes internal workings
## kube-apiserver
- talks to all the other internal components (central communication channel)
- talk to you too (when you use the cli)
## kube-schedule
- assigns pods to nodes
- configurable for resources, limits, etc.
## kube-controller-manager
- controls the things in the namespace
- consists of namespace-controller, deployment-controller, replicaset-controller, etc.
- allows "operators" a.k.a. custom controllers
- the individual controllers actually create and change the things
## kubelet
- creates containers in pod when the pod is scheduled to run
- container health checks
- uses CNI and (Docker or Rkt) to achieve these things


# install some charts?
helm install --create-namespace --namespace hello-kubernetes hello-world ./hello-kubernetes

# get the LoadBalancer ip address.
# (didn't work for me.  it returned blank)
kubectl get svc hello-kubernetes-hello-world -n hello-kubernetes -o 'jsonpath={ .status.loadBalancer.ingress[0].ip }'



# misc

helm charts have {{ variable }} and there is a values.yaml file with the values for them.

all pods can communicate with all pods and nodes without NAT

the IP a pod sees itself is the same as the IP that other pods see it as

## cgroups
they take all CPU and RAM resources and divide them into chunks, and assign processes to the chunks

## Rkt
An open-source alternative to Docker.  Supports Pods.

## affinity
Affinity is when two things should go together.  There is strong affinity (they *must* go together) and weak affinity (they *should* go together if it's not too much hassle).
Anti-affinity is the same thing, but for not going together.  Again, strong and weak.
There exists affinity for pod-pod pairs, and there exists affinity for pod-node pairs.

## SecurityContext
We can apply a SecurityContext to a container or Pod giving certain restrictions for root access and the like.
## Network Policy
You can add restrictions to the network. (by default any pod can talk to any pod

## Downward API
Allows a container to know info external to it, that is, cluster metadata, which includes the pod's IP address and name.

## ConfigMaps and Secrets
can be mounted onto containers as volumes, or alternatively can be set as environment variables.
