# Kubernetes in Virtual Machine Ansible Playbook
Deploy kubernetes (microk8s) and ArgoCD in a vagrant managed VirtualBox VM

## Requirements
* VirtualBox
* Vagrant
* Ansible
* passlib (`sudo apt install python3-passlib`)

## Usage
```bash
vagrant up
```

## Services
### Portainer
URL: http://localhost:9000
Set admin credentials on first login

### ArgoCD
URL: ArgoCD: http://localhost:8080

Credentials: admin/admin

### K8S API
Access VM cluster from host:
* Map host in local `/etc/hosts`
```
127.0.0.1    kubernetes
```

* Copy vm kube config to local (host) `~/.kube/config`
* Edit `~/.kube/config`, change
```
server: https://[IP Address]]:16443
```
into:
```
server: https://kubernetes:16443
```
