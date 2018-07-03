---
description: 'Ok, vamos subir nosso primeiro Kubernetes?'
---

# Subindo!!

## Minikube

Para fins de estudo, você pode usar o kubernets localmente na sua estação de trabalho. Para isso, utilize o projeto do minikube \(Você deve já ter visto isso na seção [anterior](./)\).

E como **iniciar** o minikube? Muito simples!!! Veja:

```bash
$ minikube start
```

Exemplo de retorno:

```text
$ minikube start
Starting local Kubernetes v1.10.0 cluster...
Starting VM...
Getting VM IP address...
Moving files into cluster...
Setting up certs...
Connecting to cluster...
Setting up kubeconfig...
Starting cluster components...
Kubectl is now configured to use the cluster.
Loading cached images from config file.

```

Para verificar o **status** do cluster, execute o comando:

```text
$ minikube status
```

Exemplo de retorno:

```text
$ minikube status
minikube: Running
cluster: Running
kubectl: Correctly Configured: pointing to minikube-vm at 192.168.99.100
```

E para **parar** o minikube:

```text
$ minikube stop
```

Exemplo de retorno:

```text
$ minikube stop
Stopping local Kubernetes cluster...
Machine stopped.
```



Um recurso MUITO útil é o dashboard \(web ui\) nativo do Kubernetes. No caso do minikube, para iniciar e acessar o dashboard execute:

```text
$ minikube dashboard
```

Você receberá um retorno parecido com esse:

```text
$ minikube dashboard
Opening kubernetes dashboard in default browser...
```

No seu browser, será aberto o respectivo dashboard.





### Resumindo

| **Comando** | **Descrição** |
| --- | --- | --- | --- | --- |
| minikube start | Iniciar o Kubernetes localmente. |
| minikube status | Obter o status do Kubernetes que está rodando localmente. |
| minikube stop | Parar o Kubernetes localmente. |
| minikube dashboard | Inicia e apresenta o dashboard web do Kubernetes |



