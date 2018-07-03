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



