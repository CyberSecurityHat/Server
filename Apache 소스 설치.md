# Apache 소스 설치

### 구축 환경
- Server OS : CentOS

<br>

1. 소스 다운로드
```
소스 다운로드 받기
```
참고 : /usr/local/src 에 저장

<br>

2. 확인 작업
```
sha256sum <fime_name>

diff <file_name> <filename>

md5 sum <file_name>

rdate -s time.bora.net # 시간 동기화
date # 시간 확인
```

<br>

3. 소스 설치 진행
```
which gcc

rpm -e httpd
rpm -e httpd* --nodeps

rpm -qa |grep httpd

cd /usr/local/src

tar jxvf <file_name>.tar.bz2
tar zxvf
tar Jxvf

cd httpd.2.4.54/

./configure --help
./configure --prefix=/usr/local/apache \
>  --enable-so   --enable-mods-shared=all

# 실패 시, 한 단계 올라가서 지우고 다시. make clean은 권장하지 않음

make && make install # make 성공 시, make install 실행
ls /usr/local/apache
ls /usr/local/apache/modules/* | wc -l

### 실패 한 경우 ###
rm -rf /usr/local/apache
cd ..
rm -rf httpd2.4.54
# 설치 재진행

ls -l /usr/local/apache/modules/* | wc -l # 설치 확인
du -sh /usr/local/apache # 설치 확인

vi /usr/local/apache/conf/httpd.conf
```

<br>

4. 환경설정파일 설정
/usr/local/apache/conf/httpd.conf
```
ServerName www.linux.com:80 # 변경
#DocumnetRoot... # 확인
#DirectoryIndex # 확인
```

<br>

5. 실행데몬 스크립트로 실행
```
/usr/local/apache/bin/apachectl start
```

<br>

참고 : 설정파일 오류를 못 찾아서 처음부터 다시 설치해야 하는 경우, 아래처럼 설정파일 지우고 다시 시작
```
cd /usr/local/apache/conf
rm httpd.conf
cp original/httpd.conf .
```