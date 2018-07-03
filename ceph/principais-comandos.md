---
description: Coletânea dos principais comandos e macetes para utilizar o CEPH
---

# Principais comandos

##  Obtendo a saúde do cluster CEPH

Para obter a saúde do seu cluster CEPH, basta utilizar o seguinte comando:

```
$ ceph -s
```

O seu retorno será algo parecido com isso e você poderá ver muitos detalhes do seu cluster, como por exemplo o espaço consumido e disponível do CEPH.

```
    cluster 2bb05945-9766-4478-a23a-eeb2940be4af
     health HEALTH_OK
     monmap e1: 2 mons at {sk8controller02=192.168.20.2:6789/0,sk8worker02=192.168.20.3:6789/0}
            election epoch 28, quorum 0,1 cephmon01,cephmon02
      fsmap e8: 1/1/1 up {0=cepmon01=up:active}, 1 up:standby
     osdmap e52: 5 osds: 5 up, 5 in
            flags sortbitwise,require_jewel_osds
      pgmap v19962: 336 pgs, 12 pools, 3538 MB data, 3437 objects
            10853 MB used, 37215 MB / 48069 MB avail
                 336 active+clean
```

##  Listando os Pools existentes

Quando queremos listar os pools existentes devemos utilizar este comando:

```
$ ceph osd lspools
```

Lembrando que quando você implementa um cluster pela primeira vez sem criar um pool, o Ceph usa os pools padrões para armazenar dados e temos estes.

```
default.rgw.control,
3 default.rgw.data.root,
4 default.rgw.gc,
5 default.rgw.log,
6 default.rgw.users.uid,
7 default.rgw.users.keys,
8 default.rgw.buckets.index,
9 default.rgw.buckets.data,
```

## Criando novos Pools

No momento que houver a necessidade de criação de um pool, precisamos executar tal comando:

```
$ ceph osd pool create <nome_do_pool> <pg_num>
```

Segue exemplo:

```
$ ceph osd pool create cephfs_data 100
```

{% hint style="info" %}
Antes de criar o pool devemos nos atentar ao pg\_num, pois ele é responsável no comportamento do cluster e durabilidade dos dados.

Segue valor recomendado no pg\_num:

Se existir menos que 5 OSD, utilizar pg\_num = "128

Entre 5 a 10 OSD,  utilizar pg\_num = "512"

Entre 10 a 50 OSD, utilizar pg\_num = "1024"

Caso tenha mais de 50 OSD, deverá realizar o cálculo manual por meio do trade-offs
{% endhint %}

Ao termino da criação podemos executar o comando que lista todos os pools, para validar sua existência.

```
root@cephmon01:/# ceph osd lspools
default.rgw.control,
3 default.rgw.data.root,
4 default.rgw.gc,
5 default.rgw.log,
6 default.rgw.users.uid,
7 default.rgw.users.keys,
8 default.rgw.buckets.index,
9 default.rgw.buckets.data,
10 cephfs_data,
```



