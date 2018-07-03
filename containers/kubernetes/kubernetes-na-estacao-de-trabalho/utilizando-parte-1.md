---
description: Vamos rodar nosso primeiro container no cluster local? O que acha??? Hein???
---

# Testando...

Se você já usou docker, deve estar familiarizado com coisa desse tipo:

```text
$ docker run --rm -it centos /bin/bash
```

O comando anterior está subindo um container docker de forma interativa e executando o bash dentro do mesmo. Você, basicamente, "cairá" dentro de uma sessão do bash que estará dentro de um container de centos. Ao sair, o container será automaticamente apagado.

E no Kubernetes? Dá para fazer isso? Claaaarrrroooooooo que sim!!! Execute ai no seu desktop \(o minikube já tem que estar instalado e rodando...\):

```text
$ kubectl run tmp-shell --rm -i --tty --image centos -- /bin/bash
```

O que aconteceu? Basicamente da mesma forma que anteriormente você executava uma sessão do bash no seu docker local, você também conseguiu executar uma sessão em um container bash no kubernets.

Para seu conhecimento, você também poderia ter executado o deploy via arquivo YAML. Seria assim:

```yaml
{
  "kind": "Deployment",
  "apiVersion": "extensions/v1beta1",
  "metadata": {
    "name": "tmp-shell-exemplo",
    "namespace": "default",
    "generation": 1,
    "labels": {
      "run": "tmp-shell-exemplo"
    },
    "annotations": {
      "deployment.kubernetes.io/revision": "1"
    }
  },
  "spec": {
    "replicas": 1,
    "selector": {
      "matchLabels": {
        "run": "tmp-shell-exemplo"
      }
    },
    "template": {
      "metadata": {
        "creationTimestamp": null,
        "labels": {
          "run": "tmp-shell-exemplo"
        }
      },
      "spec": {
        "containers": [
          {
            "name": "tmp-shell-exemplo",
            "image": "centos",
            "args": [
              "/bin/bash"
            ],
            "resources": {},
            "terminationMessagePath": "/dev/termination-log",
            "terminationMessagePolicy": "File",
            "imagePullPolicy": "Always",
            "stdin": true,
            "tty": true
          }
        ],
        "restartPolicy": "Always",
        "terminationGracePeriodSeconds": 30,
        "dnsPolicy": "ClusterFirst",
        "securityContext": {},
        "schedulerName": "default-scheduler"
      }
    },
    "strategy": {
      "type": "RollingUpdate",
      "rollingUpdate": {
        "maxUnavailable": "25%",
        "maxSurge": "25%"
      }
    },
    "revisionHistoryLimit": 2,
    "progressDeadlineSeconds": 600
  }
}
```

Sempre que possível, acompanhe seu Kubernetes via dashboard. Incialmene, a visão gráfica vai lhe ajudar a entender o que está acontecendo. Lembrando que para subir o dashboard \(web ui\) do minikube é:

```text
$ minikube dashboard
```



Se você conseguiu acessar o seu dashboard e também executar o primeiro container, possivelmente, esteja tudo certo :\)



