























How to update nerdctl version num in Rancher Desktop
---
```
rdctl shell
lima-rancher-desktop:/Users/jan$ sudo -i
lima-rancher-desktop:~# wget https://github.com/containerd/nerdctl/releases/download/v0.21.0/nerdctl-0.21.0-linux-amd64.tar.gz
[...]
'nerdctl-0.21.0-linux-amd64.tar.gz' saved
lima-rancher-desktop:~# export CONTAINERD_ADDRESS=/run/k3s/containerd/containerd.sock
lima-rancher-desktop:~# nerdctl version
Client:
 Version:   v0.20.0
[...]
lima-rancher-desktop:~# tar xvfz nerdctl-0.21.0-linux-amd64.tar.gz -C /usr/local/bin nerdctl
nerdctl
lima-rancher-desktop:~# nerdctl version
Client:
 Version:   v0.21.0
[...]
lima-rancher-desktop:~# rm nerdctl-0.21.0-linux-amd64.tar.gz
```
