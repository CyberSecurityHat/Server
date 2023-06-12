# NFT 서버 구축

### 구축 환경
- Server OS : CentOS7

<br>

```
# rpm -q rpcbind nfs-utils
# yum install rpcbind nfs-utils
# mkdir [공유 디렉토리 설정 파일]
# chmod 1777 [공유 디렉토리 설정 파일]
# touch [공유 디렉토리 설정 파일]/[파일 이름]
# vi /etc/exports
```

<br>

/etc/exports
```
[디렉토리 경로]	[대상 아이피]
```

<br>

```
# systemctl stop firewalld
# systemctl start rpcbind nfs-server
# systemctl -l status rpcbind nfs-server
# ps aux |egrep 'rpcinfo | nfs-server'
# systemctl enable rpcinfo nfs-server
# mount -t nfs [SERVER IP]:[마운트 디렉토리 경로] /mnt
# rpcinfo
# exportfs -v
# showmount -e [SERVER IP]
# nfsstat
# mount |grep nfs
# touch /mnt/nfs-text.txt
# vi /etc/fstab
```

<br>

/etc/fstab
```
[SERVER IP]:/[마운트 디렉토리 경로]		/mnt	nfs	timeo=15,soft,retrans=3	0 0
```