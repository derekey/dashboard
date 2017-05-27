# Kubernetes Dashboard
[![Build Status](https://travis-ci.org/kubernetes/dashboard.svg?branch=master)](https://travis-ci.org/kubernetes/dashboard)
[![Coverage Status](https://codecov.io/github/kubernetes/dashboard/coverage.svg?branch=master)](https://codecov.io/github/kubernetes/dashboard?branch=master)
[![Go Report Card](https://goreportcard.com/badge/github.com/kubernetes/dashboard)](https://goreportcard.com/report/github.com/kubernetes/dashboard)
[![GitHub release](https://img.shields.io/github/release/kubernetes/dashboard.svg)](https://github.com/kubernetes/dashboard/releases/latest)

Kubernetes Dashboard 是一个用于 Kubernetes 集群的通用web用户界面，允许用户管理和维护运行在集群上的应用，以及集群本身。

![Dashboard UI workloads page](docs/dashboard-ui.png)

## 部署dashboard
It is likely that the Dashboard is already installed on your cluster. Check with the following command:
```shell
$ kubectl get pods --all-namespaces | grep dashboard
```

If it is missing, you can install the latest stable release by running the following command:
```shell
$ kubectl create -f https://git.io/kube-dashboard
```

If you are using Kubernetes 1.5 or earlier, you can install the latest stable release by running the following command:
```shell
$ kubectl create -f https://git.io/kube-dashboard-no-rbac
```

You can also install unstable HEAD builds with the newest features that the team works on by
following the [development guide](docs/devel/head-releases.md).

Note that for the metrics and graphs to be available you need to
have [Heapster](https://github.com/kubernetes/heapster/) running in your cluster.

## dashboard 使用
The easiest way to access Dashboard is to use kubectl. Run the following command in your desktop environment:
```shell
$ kubectl proxy
```
kubectl will handle authentication with apiserver and make Dashboard available at [http://localhost:8001/ui](http://localhost:8001/ui)

The UI can _only_ be accessed from the machine where the command is executed. See `kubectl proxy --help` for more options.

## 另一种用法
You may access the UI directly via the apiserver proxy. Open a browser and navigate to `https://<kubernetes-master>/ui`.

Please note, this works only if the apiserver is set up to allow authentication with username and password. This is not currently the case with the setup tool `kubeadm`. See [documentation](http://kubernetes.io/docs/admin/authentication/) if you want to configure it manually.

If the username and password is configured but unknown to you, then use `kubectl config view` to find it.

## 文档

* [User Guide](http://kubernetes.io/docs/user-guide/ui/): Entry-level overview

* [开发指南](docs/devel/README.md): 给二次开发的开发者

* [Design Guide](docs/design/README.md): For anyone interested in contributing _design_ (less technical)

* [Troubleshooting Guide](docs/user-guide/troubleshooting.md): Common issues encountered while setting up Dashboard

## 许可

The work done has been licensed under Apache License 2.0. The license file can be found
[here](LICENSE). You can find out more about the license at:

http://www.apache.org/licenses/LICENSE-2.0
