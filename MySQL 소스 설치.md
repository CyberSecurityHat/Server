# MySQL 소스 설치

1. 소스 파일 다운로드 및 압축풀기
```
# tar -zxvf
```

2. 설치 스크립트 작성

/usr/local/src/mysql-5.7.39/con.sh
```
cmake . \
 -DDOWNLOAD_BOOST=1 \
 -DWITH_BOOST=/usr/local/src/mysql5.7.39/boost
```

3. 설치
/usr/local/src/mysql-5.7.39/
```
# sh con.sh
# make install
```

4. 설치 확인
```
# du -sh /usr/local/mysql
```

5. MySQL 계정 접속
```
# cd /usr/local/mysql
# cd bin
# ./mysqld --initialize --user=root
# ./mysqld_safe --user=root & # 백그라운드 실행
# > alter user 'root'@localhost' identified by '1234';
# > flush privileges;
# > quit
# ./mysql -p '1234'
```

6. mysql 패스워드 초기화(처음에만 사용. DB 날라감)
```
# rm -rf ../data
# pkill -9
# ps aux | grep mysql
# ./mysqld --initialize --user=root
```