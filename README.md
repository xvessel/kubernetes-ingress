## Kubernetes Ingress Controller

### 安装

在Kubernetes集群的Master节点执行以下命令(该yaml文件来自[Nginx-Controller官方仓库](https://github.com/kubernetes/ingress-nginx/blob/master/deploy/static/mandatory.yaml)):
```
$ kubectl apply -f ./ingress-nginx-mandatory.yaml
```

### 跟官方库yaml区别

1. Controller从Deployment部署方式换成DaemonSet方式

2. Pod的网络方式设置为

```
      hostNetwork: true
```

3. Pod的调度策略允许创建在Kubernetes Master节点

```
      tolerations:
      - key: node-role.kubernetes.io/master
        effect: NoSchedule
```
