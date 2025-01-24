# k8s-install-minikube

minikube 

## minikube 버전 확인

```shell
# minikube 버전 확인
minikube version
```

## minikube driver 확인

```shell
# minikube driver 확인
minikube config get driver
```

## minikube driver 셋팅

```shell
# minikube 기본 driver 설정 -> docker 런타임 환경 사용
# 로컬에서 docker가 구동중이어야 함
$ minikube config set driver docker
```

## minikube 실행

```shell
# minikube 실행
minikube start --cpus=2 --memory=4g --disk-size=100g --driver=docker --kubernetes-version=v1.28
```

## minikube 상태 확인

```shell
minikube status
```

## k8s context 확인

```shell
# k8s context 확인
# context란 클러스터, 사용자, 네임스페이스 정보를 사용하기 위한 커멘드이다
# 쉽게 말해 k8s 클러스터에 연결된 환경 설정이라 보면 된다
$ kubectl config get-contexts
CURRENT   NAME             CLUSTER          AUTHINFO         NAMESPACE
          docker-desktop   docker-desktop   docker-desktop
*         minikube         minikube         minikube         default

# k8s node 확인
$ kubectl get nodes
NAME       STATUS   ROLES           AGE     VERSION
minikube   Ready    control-plane   7m17s   v1.28.15

# k8s pod 확인
$ kubectl get po -o wide -A
NAMESPACE     NAME                               READY   STATUS    RESTARTS        AGE     IP             NODE       NOMINATED NODE   READINESS GATES
kube-system   coredns-5dd5756b68-pthrd           1/1     Running   0               8m19s   10.244.0.2     minikube   <none>           <none>
kube-system   etcd-minikube                      1/1     Running   0               8m31s   192.168.49.2   minikube   <none>           <none>
kube-system   kube-apiserver-minikube            1/1     Running   0               8m34s   192.168.49.2   minikube   <none>           <none>
kube-system   kube-controller-manager-minikube   1/1     Running   0               8m34s   192.168.49.2   minikube   <none>           <none>
kube-system   kube-proxy-8kb6b                   1/1     Running   0               8m19s   192.168.49.2   minikube   <none>           <none>
kube-system   kube-scheduler-minikube            1/1     Running   0               8m31s   192.168.49.2   minikube   <none>           <none>
kube-system   storage-provisioner                1/1     Running   1 (7m54s ago)   8m28s   192.168.49.2   minikube   <none>           <none>
```