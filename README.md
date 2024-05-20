# k8s-workshop-in-action

## Prerequisites software

### docker
- [Macos](https://docs.docker.com/desktop/install/mac-install/)
- [Windows](https://docs.docker.com/desktop/install/windows-install/)


Start Docker Destop then open terminal for check docker work 
```
docker version
```

Output should display `Client` and `Server` like this
```
Client:
 Version:           25.0.4-rd
 API version:       1.43 (downgraded from 1.44)
 Go version:        go1.21.8
 Git commit:        c4cd0a9
 Built:             Fri Mar  8 09:09:07 2024
 OS/Arch:           darwin/amd64
 Context:           orbstack

Server: Docker Engine - Community
 Engine:
  Version:          24.0.6
  API version:      1.43 (minimum version 1.12)
  Go version:       go1.20.7
  Git commit:       1a79695
  Built:            Mon Sep  4 12:32:17 2023
  OS/Arch:          linux/amd64
  Experimental:     false
 containerd:
  Version:          v1.7.6
  GitCommit:        091922f03c2762540fd057fba91260237ff86acb
 runc:
  Version:          1.1.9
  GitCommit:        82f18fe0e44a59034f3e1f45e475fa5636e539aa
 docker-init:
  Version:          0.19.0
  GitCommit:        de40ad0
```

---

### k3d
Websit: https://k3d.io/

#### Install on Macos

Run command
```
brew install k3d
```

#### Install on Windows

The easiest way to get k3d running on Windows is with Chocolatey. To install Chocolatey you can run the following from an administrative PowerShell instance:

```shell
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
```

Now close PowerShell and open a new administrative instance and run the following to install k3d and a couple other useful tools:

```shell
choco install k3d -y
choco install jq -y
choco install yq -y
choco install kubernetes-helm -y
```

Check k3d work 
```
k3d --help
```

---

### kubectl
- [Macos](https://kubernetes.io/docs/tasks/tools/install-kubectl-macos/)
- [Windows](https://kubernetes.io/docs/tasks/tools/install-kubectl-windows/)

Check kubectl work 
```
kubectl --help
```

## Make sure it's work

Before workshop please ensure your machine and setup all it works.

### Create cluster
Running below command for create cluster
```
k3d cluster create my-cluster --servers 1 --agents 3 --port "8888:80@loadbalancer" --port "8889:443@loadbalancer"
```

Checking cluster
```
kubectl get node
```

The output should be like this
```
NAME                      STATUS   ROLES                  AGE   VERSION
k3d-my-cluster-server-0   Ready    control-plane,master   53s   v1.27.4+k3s1
k3d-my-cluster-agent-1    Ready    <none>                 49s   v1.27.4+k3s1
k3d-my-cluster-agent-0    Ready    <none>                 48s   v1.27.4+k3s1
k3d-my-cluster-agent-2    Ready    <none>                 48s   v1.27.4+k3s1
```

### Running application
Try to running sample application. For example running nginx

Running below command
```
kubectl run my-nginx --image nginx:1.25.4
```

Checking application was run
```
kubectl get pod
```

The output should be like this
```
NAME       READY   STATUS    RESTARTS   AGE
my-nginx   1/1     Running   0          30s
```

The status must be **Running**

> [!IMPORTANT]  
> **If all it's work. Your machine already for the workshop.**

Remove cluster
```
k3d cluster delete my-cluster
```