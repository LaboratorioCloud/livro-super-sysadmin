# CEPH como S3?

Uma das grandes magnitudes do CEPH é a possibilidade de utilizar seu storage como S3.  

Para criar um usuário de S3:

```
$ radosgw-admin user create --uid="usuario" --display-name="Primeiro Usuario"
```

Segue retorno após criação:

```
{
  "user_id": "usuario",
  "display_name": "Primeiro Usuario",
  "email": "",
  "suspended": 0,
  "max_buckets": 1000,
  "auid": 0,
  "subusers": [],
  "keys": [
    {
      "user": "usuario",
      "access_key": "0MPINSZ803F2TRWP3TDE",
      "secret_key": "DxntFGnUg6ylQSeftdVWdPEOnjooVbNHw2zj5qMK"
    }
  ],
  "swift_keys": [],
  "caps": [],
  "op_mask": "read, write, delete",
  "default_placement": "",
  "placement_tags": [],
  "bucket_quota": {
    "enabled": false,
    "max_size_kb": -1,
    "max_objects": -1
  },
  "user_quota": {
    "enabled": false,
    "max_size_kb": -1,
    "max_objects": -1
  },
  "temp_url_keys": []
} 
```

{% hint style="info" %}
```
Armazene as credenciais geradas para consumo do S3:

"access_key": "0MPINSZ803F2TRWP3TDE",
"secret_key": "DxntFGnUg6ylQSeftdVWdPEOnjooVbNHw2zj5qMK"
```
{% endhint %}

## Criando e utilizando Bucket com Python

Para criar seu primeiro bucket com python, primeiramente precisaremos de utilizar o boto.

{% hint style="info" %}
```
O  Boto é um pacote do Python que fornece interfaces 
para o Amazon Web Services. Atualmente, todos os 
recursos funcionam com o Python 2.6 e 2.7.
```
{% endhint %}

#### CENTOS

```
$ sudo yum install python-boto -y
```

#### UBUNTU/DEBIAN

```
$ sudo apt-get install python-boto/xenial -y
```

Criei um script chamado **s3test.py** e insira as seguintes linhas, lembrando que deve-se inserir suas credenciais.

```
import boto.s3.connection

access_key = '0MPINSZ803F2TRWP3TDE'
secret_key = 'DxntFGnUg6ylQSeftdVWdPEOnjooVbNHw2zj5qMK'
conn = boto.connect_s3(
        aws_access_key_id=access_key,
        aws_secret_access_key=secret_key,
        host='<ip_cephmon01>', port=7480,
        is_secure=False, calling_format=boto.s3.connection.OrdinaryCallingFormat(),
       )

bucket = conn.create_bucket('nome_bucket')
for bucket in conn.get_all_buckets():
    print "{name} {created}".format(
        name=bucket.name,
        created=bucket.creation_date,
    )
```

Com o seu script criado agora é a hora de executa-lo:

```
root@webpx01:~# python s3test.py
nome_bucket 2018-07-02T21:38:06.162Z
```

Criando script para consultar os buckets existentes:

```
import boto.s3.connection

access_key = '0MPINSZ803F2TRWP3TDE'
secret_key = 'DxntFGnUg6ylQSeftdVWdPEOnjooVbNHw2zj5qMK'
conn = boto.connect_s3(
            aws_access_key_id=access_key,
            aws_secret_access_key=secret_key,
            host='<ip_cephmon01>', port=7480,
            is_secure=False, calling_format=boto.s3.connection.OrdinaryCallingFormat(),
            )

bucket = conn.get_all_buckets()
print ("Segues buckets existentes: ", bucket)
```

Execute o script e verifique se seu bucket foi criado com sucesso:

```
root@sk8admin:~# python s3list.py
('Segues buckets existentes: ', [])
```



