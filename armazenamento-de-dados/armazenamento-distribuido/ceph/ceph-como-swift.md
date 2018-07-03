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



