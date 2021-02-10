# k8s_profsummit_2021_talk


## Dev machine setup in Ubuntu MicroK8S

- Install microk8s with the following command,

```
sudo snap install microk8s --classic --channel=1.19
```

- Enable DNS addon

```
microk8s enable dns
```

- Add current user to microk8s group

```
sudo usermod -aG microk8s $USER
newgrp microk8s
```

- Add alias to .bashrc

```
alias k='microk8s kubectl'
alias helm='microk8s helm3'
```

- Make kube folder accessible

```
cd $HOME
mkdir .kube
cd .kube
microk8s config > config
```

- Run some commands to verify

```
# should list 1 node
k get nodes 

# should list NO RESOURCES
k get pods
```

## Run a Hello World App

- Run Deployment

```
k apply -f examples/kube/deployment.yaml
```

- Verify pods

```
k get po

k describe po <POD_ID>
```

- Run SVC

```
k apply -f examples/kube/svc.yaml
```

- Verify svc

```
k get svc
```

- Hit CURL to verify

```
curl -v http://<SVC_CLUSTER_IP>:3000
```
