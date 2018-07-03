---
description: Vamos rodar nosso primeiro container no cluster local? O que acha??? Hein???
---

# Utilizando \(parte 1\)

Se você já usou docker, deve estar familiarizado com coisa desse tipo:

```text
$ docker run --rm -it centos /bin/bash
```

O comando anterior está subindo um container docker de forma interativa e executando o bash dentro do mesmo. Você, basicamente, "cairá" dentro de uma sessão do bash que estará dentro de um container de centos. Ao sair, o container será automaticamente apagado.

E no Kubernetes? Dá para fazer isso? Claaaarrrroooooooo que sim!!! Execute ai no seu desktop \(o minikube já tem que estar instalado e rodando...\):

```text
$ kubectl run tmp-shell --rm -i --tty --image centos -- /bin/bash
```



