# CEPH como SWIFT?

Além do S3 também podemos utilizar o SWIFT.  

Para criar um usuário de SWIFT:

```
$ radosgw-admin user create --subuser=usuario:swf0001 --display-name="Usuario" --key-type=swift --access=full
```

Segue retorno após criação:

```
{
    "user_id": "usuario",
    "display_name": "Usuario",
    "email": "",
    "suspended": 0,
    "max_buckets": 1000,
    "auid": 0,
    "subusers": [
        {
            "id": "usuario:swf0001",
            "permissions": "full-control"
        }
    ],
    "keys": [],
    "swift_keys": [
        {
            "user": "testuser:swf0001",
            "secret_key": "5iskYXPQ7UopX5fq8ltNU857TcdOStcUuQDwkuPW"
        }
    ],
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

## Criando Bucket com Python

Para criar seu primeiro bucket com python, primeiramente precisaremos de utilizar o boto.

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

