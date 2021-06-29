docker images --> list all images
docker ps --> list running containers
docker ps -a --> list all containers


docker push {imagename}  -->  push an image to docker hub.  Make sure image name starts with 'mvlancellotti/'
docker pull --> pull an image from the internet



`docker run --rm` --> create container from image and run it
`docker run --rm -v $(pwd):/home/jovyan` --> mount host dir ("volume") . at docker container dir /home/jovyan
docker stop --> pause a running container
docker start --> resume a paused container
docker exec {cntner} {cmd} --> execute a command in a running container
docker exec -it {container} bash --> get a tty into the container! (or sh)





docker commit {containername} {imagename} --> create image out of current container state.
docker login --> login to docker.com / docker hub, so that you can push images to it

# logging!
docker logs --tail=50 {container} --> fetch logs for your application!
docker logs --follow {container} --> get logs that automatically update






Dockerfile notes
-----------------------
# copy a file in
COPY host/computer/file.py /container/file.py
COPY host/computer/file.py /container/.

# first arg of '.' indicates entire directory
COPY . /container/dir

# second arg of '.' indicates '~/.' for each file

COPY . .







swarm tutorial:
https://docs.docker.com/engine/swarm/swarm-tutorial/




Docker Compose notes
-------------------------
docker-compose.yml specification: https://github.com/compose-spec/compose-spec/blob/master/build.md






Kubernetes
-------------

## great video:
https://vimeo.com/245778144/4d1d597c5e

## kery terms:
pod - "meta container". (containers typically different) Could contain single docker container, or a few that need to work together. For example, an app in one container, and a sibling app that collects performance metrics in another, all together in one pod.
deployment - "meta pod". (pods typically identical) multiple pods running with load balancing and fault tolerance
namespace - contains deployment, replica-set, serviceaccount, secret, nodes
service - port forwarder and load balancer to the pods
ingress - point hostname to service IP address



minikube start  -  start your 1-node cluster
minikube dashboard  -  see dashboard
kubectl get po -A  -  see all running processes? or pods?

kubectl create deployment hello-minikube --image=k8s.gcr.io/echoserver:1.4
kubectl expose deployment hello-minikube --type=NodePort --port=8080

kubectl get services hello-minikube

kubectl create namespace <name>
kubectl create -f resource.yaml  ->  to create more complicated things, specify in a yaml


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
## check on everything
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
