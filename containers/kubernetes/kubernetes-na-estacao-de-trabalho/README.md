---
description: >-
  A melhor forma para iniciar os estudos é instalar o Kubernetes localmente na
  sua estação de trabalho. Sim, e não se preocupe, isso não será difícil (ou não
  como instalar um Kubernetes em produção)
---

# Na estação de trabalho?

A visão geral é a seguinte:

* Você irá precisar do minikube. 
* Também terá que instalar o kubectl

Resumindo... 

### Minikube

Trata-se de um projeto mantido pelo próprio Kubernetes. De uma forma simples, o minikube server para rodar um cluster de Kubernetes de apenas um nó na sua estação de trabalho.

Para instalar, utilize o procedimento oficial do projeto, que pode ser acessado aqui: [https://github.com/kubernetes/minikube/](https://github.com/kubernetes/minikube).

Basicamente, o minikube irá usar o seu sistema nativo de virtualização \(exemplo: Virtualbox\) para poder rodar uma VM e, dentro dela, instalar o necessário para poder rodar um Kubernetes.



### Kubectl

O kubectl é a ferramentar de linha de comando utilizado para realizar o deploy e gerenciar as aplicações que estarão rodando dentro do Kubernetes. Para a instalação dele, também siga a documentação oficial: [https://kubernetes.io/docs/tasks/tools/install-kubectl/](https://kubernetes.io/docs/tasks/tools/install-kubectl/)



{% hint style="danger" %}
Sempre siga as instruções oficiais de instalação. Evitem seguir instuições de fontes não oficiais ou de terceiros. Caso tenha problema em instalar algo pode entrar em contato conosco suporte@laboratorio.cloud
{% endhint %}

