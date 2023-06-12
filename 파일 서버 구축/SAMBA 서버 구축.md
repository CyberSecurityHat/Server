# SAMBA 서버 구축

### 구축 환경
- Server OS : Cent OS7

<br>

```
# rpm -q samba samba-common -samba-client
# yum search sambayum
# yum install samba samba-common -samba-client
# mkdir [공유 디렉터리 경로]
# chmod 1777 [공유 디렉터리 경로]
vi /etc/samba/smb.conf
```

<br>

/etc/samba/smb.conf
```
public = yes
```
참고 : 모든 사용자가 접근 가능하게 할 경우 추가

<br>

```
# testparm
# smbpasswd -a [사용자 계정
# systemctl stop firewalld
# setenforce 0
# getenforce
# systemctl start smb nmb
# ps aux |egrep 'smb|nmb'
# systemctl -l status smb nmb
# systemctl enable snb nmb
```
참고 : smbpasswd -a 는 삼바 사용자로 추가하며, -a 옵션 제거시, 기존 사용자의 비밀번호 변경

<br>

Windows Client 접속
```
1. 단축키 Win + R 입력
2. \\[SERVER IP]
```