# ETS240vmh001P
- 概要

内製開発用の仮想環境ホスティングサーバ01号機である。

- ホストサーバスペック
  - 本体：DL360 Gen10 8SFF
  - CPU：XeonS 4116 2.1GHz 1P12C
  - メモリ：32Gb
  - HDD：1Tb × 2
  - RAID：1
  - 保守：3年間保守(202002-202302) | HPEファウンデーションケア24×7
***

- ゲストサーバスペック

| HOST | ETS240vmh001P | ETS240vmh002P | ETS240vmh003P | ETS240vmh004P |
| ------ | :------: | :------: | :------: | :------: |
| コア数 | 1 | 4 | 2 | 2 |
| メモリ | 2Gb | 8Gb | 4Gb | 2Gb |
| ストレージ | 200Gb | 200Gb | 200Gb | 100Gb |

***

- ネットワーク

eth1とeth3でボンディングしており、ブリッジネットワークとしている。
```
[setupuser@ETS240vmh001p network-scripts]$ cat ifcfg-bond-bond0
BONDING_OPTS=mode=active-backup
TYPE=Bond
BONDING_MASTER=yes
PROXY_METHOD=none
BROWSER_ONLY=no
DEFROUTE=yes
IPV4_FAILURE_FATAL=no
NAME=bond-bond0
UUID=3d2b52ac-4ff2-4a70-b14a-567b22613032
DEVICE=bond0
ONBOOT=yes
BRIDGE=br0
```
```
[setupuser@ETS240vmh001p network-scripts]$ cat ifcfg-bridge-br0
STP=no
TYPE=Bridge
PROXY_METHOD=none
BROWSER_ONLY=no
BOOTPROTO=none
DEFROUTE=yes
IPV4_FAILURE_FATAL=no
#IPV6INIT=yes
#IPV6_AUTOCONF=yes
#IPV6_DEFROUTE=yes
#IPV6_FAILURE_FATAL=no
#IPV6_ADDR_GEN_MODE=stable-privacy
NAME=bridge-br0
UUID=36238747-12e4-4791-9bc6-ae647789dcee
DEVICE=br0
ONBOOT=yes
IPADDR=192.168.240.53
PREFIX=24
GATEWAY=192.168.240.21
#DNS1=192.168.240.1
```

| ETS240vmh001P-iLO | ETS240vmh001P | ETS240dev001P | ETS240dev002P | ETS240dev003P | ETS240dev004P |
| :------: | :------: | :------: | :------: | :------: | :------: |
| 192.168.240.52 | 192.168.240.53 | 192.168.240.54 | 192.168.240.55 | 192.168.240.56 | 192.168.240.57 |
***
>個別の設定情報はwikiに記載
