# Configurações de Hardware

## CEPH-OSD

| Criteria | Minimum Recommended |
| --- | --- | --- | --- | --- | --- |
| Processor | 1x 64-bit AMD-64  1x 32-bit ARM dual-core or better  1x i386 dual-core |
| RAM | ~1GB for 1TB of storage per daemon |
| Volume Storage | 1x storage drive per daemon |
| Journal | 1x SSD partition per daemon \(optional\) |
| Network | 2x 1GB Ethernet NICs |

## CEPH-MON

| Criteria | Minimum Recommended |
| --- | --- | --- | --- | --- |
|  Processor | 1x 64-bit AMD-64/i386  1x 32-bit ARM dual-core or better  1x i386 dual-core |
| RAM | 1 GB per daemon |
| Disk Space | 10 GB per daemon |
| Network | 2x 1GB Ethernet NICs |

## CEPH-MDS

| Criteria | Minimum Recommended |
| --- | --- | --- | --- | --- |
|  Processor | 1x 64-bit AMD-64 quad-core  1x 32-bit ARM quad-core  1x i386 quad-core |
| RAM | 1 GB minimum per daemon |
| Disk Space | 1 MB per daemon |
| Network | 2x 1GB Ethernet NICs |

{% hint style="info" %}
Se você estiver executando um OSD com um único disco, crie uma partição para o armazenamento de volume separada da partição que contém o sistema operacional.
{% endhint %}

