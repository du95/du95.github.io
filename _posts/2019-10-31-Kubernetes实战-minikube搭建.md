---
layout: post           
title: Kubernetes实战-minikube单节点集群搭建   
date: 2019-10-31
categories: kubernetes
tags: kubernetes
excerpt: 使用minikube搭建单节点集群，创建k8s开发、实验环境，入门之旅       
---    

## 联机部署minikube  

> 环境：虚拟机ubuntu18.04，选择Linux安装环境，模拟bare-metal即裸金属服务器。   

参考地址： 

https://kubernetes.io/docs/tasks/tools/install-minikube/ 

https://minikube.sigs.k8s.io/docs/start/linux/  

注意：自备梯子，方便很多。为虚拟机、apt、docker分别配置http代理   



### Direct下载后安装 

下载并安装在/usr/local/bin/ 

``` 
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 \
   && sudo install minikube-linux-amd64 /usr/local/bin/minikube
```




### 运行minikube 

```

sudo minikube start 

```

### 运行k8s-dashboard 

使用 --url模式，会以返回dashboard访问地址的形式，而不是调用浏览器的形式访问。 

```

sudo minikube dashboard --url 

```

发挥的url为本地回环地址，minikube暴露的dashboard访问地址无法在虚拟机外直接访问，又因为使用的虚拟机模式运行的minikube，没有安装图形界面。所以需要通过kubectl配置代理才能访问 

```

sudo kubectl proxy --address='0.0.0.0' --port 8080 

```

在虚拟机外部浏览器输入刚刚返回的url，将其中ip替换为实际ip地址、端口替换为8080，就可以访问了 

### 查看kube、docker运行状态 

```

sudo kubectl get service 

sudo kubectl get node 

sudo kubectl get pods 

sudo kubectl get namespace 

sudo docker ps -l 

```

**开启K8s之旅**

```

```