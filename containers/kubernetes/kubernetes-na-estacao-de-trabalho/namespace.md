---
description: >-
  Incrivelmente, o Kubernetes suporta vários clusters virtuais dentro de um
  mesmo cluster físico. Esses clusters virtuais são chamados de namespaces. Sim,
  eu sei... isso é maravilhoso.
---

# Namespace

{% hint style="info" %}
As informações dessa sessão, quase que completamente, foi baseada na documentação oficial. Como sempre, recomendamos que você leia sempre a documentação oficial. No caso de namespaces, comece em: [https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/](https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/)
{% endhint %}

Os namespaces são destinados ao uso em ambientes com muitos usuários espalhados por várias equipes ou projetos. É uma ótima forma de dividir os espaços de trabalho.

Comece a usar namespaces quando precisar dos recursos que eles fornecem. Namespaces fornecem um escopo para nomes. Os nomes dos recursos precisam ser exclusivos em um namespace, mas não nos namespaces. 

Outro ponto importantíssimo: Namespaces são uma maneira de dividir recursos de cluster entre vários usuários \(por meio de cota de recursos\).

Segundo a recomedação do documentação do Kubernetes, não é necessário usar vários namespaces apenas para separar recursos ligeiramente diferentes, como versões diferentes do mesmo software: use rótulos para distinguir recursos dentro do mesmo namespace.

## Listar os namespaces existentes

Para listar os namespaces existentes é muito fácil, basta executar:

```text
$ kubectl get namespaces
```

Isso irá lhe retornar algo parecido com isso:

```text
$ kubectl get namespaces
NAME          STATUS    AGE
default       Active    2h
kube-public   Active    2h
kube-system   Active    2h
```

Por padrão, todo Kubernetes inicialmente possui os namespaces defaul, kube-public e kube-system. Sendo:

* **default**: O namespace padrão para objetos - ele é criado inicialmente quando você implanta um Kubernetes. Se você não criar outro ou alterar, ficarão nele os seus deploys, aplicações, etc..
* **kube-system:**  É o namespace que aloca os objetos do próprio sistema.
* **kube-public:** Este namespace é criado automaticamente e legível por todos os usuários \(incluindo aqueles não autenticados\). Esse namespace é reservado principalmente para o uso do cluster, no caso de alguns recursos serem visíveis e legíveis publicamente em todo o cluster. **O aspecto público desse namespace é apenas uma convenção, não um requisito**.

## Criar um novo namespace

É muito simples criar um novo namespace. Basicamente, você precisa apenas o kubectl configurado e apontando para o seu cluster Kubernetes. Para criar, execute o seguinte comando \(altere o parâmetro **&lt;NOME&gt;** de acordo com o nome que você quer dar para o namespace\):

```text
$ kubectl create namespace <NOME>
```

Listando novamente, você deve conseguir ver o novo namespace. Lembrando que, para listar os namespaces é:

```text
$ kubectl get namespaces
```

## Como usar o novo namespace

Você tem duas opções para utilizar o novo namespace:

* **OPÇÃO 1**: Utilizar o namespace como parâmetro em cada chamada do kubectl; OU
* **OPÇÃO 2:**  Alterar a configuração de contexto do kubectl

Vamos avaliar os dois modos...





### OPÇÃO 1: Indicando o namespace por meio de parâmetro

TODO: descrever

### OPÇÃO 2: Alterando o contexto 

TODO: descrever

