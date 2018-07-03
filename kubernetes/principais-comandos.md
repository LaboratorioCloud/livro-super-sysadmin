---
description: >-
  Veremos aqui a coletânea dos principais comandos e macetes para utilizar o
  kubernetes
---

# Principais comandos

## Visão geral da saúde do ambiente

Uma das principais tarefas de um sysadmin é verificar a saúde do ambiente. Segue os principais comandos para tal:

| **Comando** | **Principal função** |
| --- | --- | --- | --- | --- |
| kubectl get nodes | Lista os nodes do cluster em questão |
| kubectl get pods | Lista os pods |
| kubectl get deployments | Estado dos "deployments" |
| kubectl describe deployment &lt;nome&gt; | Obter dados detalhados de determinado deploy |

## Iniciar localmente - minikube

Para fins de estudo, você pode usar o kubernets localmente na sua estação de trabalho. Para isso, utilize o projeto do minikube.

Para instalar o minikube, siga as orientações de

