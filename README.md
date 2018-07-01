# Automating-selenium-kubernettes-helm
This repo provides the direction launching a [Selenium](http://www.seleniumhq.org/) deployment on a [Kubernetes](http://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager.

Kubernetes is a platform for hosting Docker containers in a clustered environment with multiple Docker hosts. Kubernetes is a system for managing containerized applications across a cluster of nodes.

![Selenium Architecture](images/Selenium-Grid-Architecture.png "Figure 1")


## Common Terms
- Pod: A group of containers
- Labels: Labels for identifying pods
- Kubelet: Container Agent
- etcd: A metadata service
- Proxy: A load balancer for pods
- Replication Controller: Manages replication of pods

### Launching selenium hub
```
$ kubectl run selenium-hub --image selenium/hub:3.4.0 --port 4444
```

### Exposing selenium-hub to be able to access externally
```
$ kubectl expose deployment selenium-hub --type=NodePort
```

### Bringing up Selenium Nodes
```
$ kubectl run selenium-node-chrome --image selenium/node-chrome:3.4.0 --env="HUB_PORT_4444_TCP_ADDR=selenium-hub" --env="HUB_PORT_4444_TCP_PORT=4444"
```

```
$ kubectl run selenium-node-firefox --image selenium/node-firefox:3.4.0 --env="HUB_PORT_4444_TCP_ADDR=selenium-hub" --env="HUB_PORT_4444_TCP_PORT=4444"
```
### Scaling Selenium Grid cluster
```
$ kubectl run selenium-node-chrome --image selenium/node-chrome:3.4.0 --env="HUB_PORT_4444_TCP_ADDR=selenium-hub" --env="HUB_PORT_4444_TCP_PORT=4444"
```

### Launch a Selenium hub
```
$ kubectl -f create selenium-hub-rc.yaml
```
#### Selenium hub as a service for nodes to connect
```
kubectl create -f selenium-hub-svc.yml
```

### Bringing up Selenium nodes
#### Chrome
```
$kubectl create -f selenium-node-chrome-rc.yaml
```
#### Firefox
```
$kubectl create -f selenium-node-firefox-rc.yaml
```

## _Using Helm_

Helm is a tool that streamlines installing and managing Kubernetes applications. 
Think of it like apt/yum/homebrew for Kubernetes.

- A Helm package is bundled up as a chart.
- Charts are Helm packages that contain at least two things:
    - A description of the package (Chart.yaml)
    - One or more templates, which contain Kubernetes manifest files

- Charts can be stored on disk, or fetched from remote chart repositories (like Debian or RedHat packages) it users git 
under the hood

#### Helm package can be found here: [helm-selenium ](https://kubeapps.com/charts/stable/selenium)

The command deploys Selenium on the Kubernetes cluster in the default configuration. The configuration section lists the parameters that can be configured during installation. 

This chart bootstraps a Selenium deployment on a Kubernetes cluster using the Helm package manager.
