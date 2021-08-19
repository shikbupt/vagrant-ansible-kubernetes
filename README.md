# vagrant-ansible-kubernetes
Combination of Vagrant and Ansible to spin up a Kubernetes cluster. 
Optimization for using in China.
Test in Vagrant 2.2.17 & VirtualBox v6.1.24

### Prerequisites
- Vagrant
- Ansible
- Proxy access to the outside

### Define amount of nodes
in Vagrantfile:
```
N = 2
```

### Set the proxy
in master-playbook.yml and node-playbook.yml
```
proxy_ip: xx.xx.xx.xx:xx
```


### Spin up cluster
```
$ vagrant up
```

### Verify on master
```
$ vagrant ssh k8s-master
$ kubectl get nodes
NAME         STATUS   ROLES                  AGE     VERSION
k8s-master   Ready    control-plane,master   10m     v1.21.0
node-1       Ready    <none>                 7m21s   v1.21.0
node-2       Ready    <none>                 4m37s   v1.21.0
```

### Install dashboard
```
kubectl apply -f dashboard.yaml
```

### Set dashboard user
```
kubectl apply -f dash-admin-user.yaml
```
