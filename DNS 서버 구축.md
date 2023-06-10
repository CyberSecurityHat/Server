# DNS 서버 구축

### 구축 환경
- Server OS : CentOS7
- Server IP : 200.168.123.10
- Domain : example.com
- Owner : CyberSecurityHat

<br>

```
rpm -q bind
yum install bind
rpm -qi bind
rpm -qc bind
```

/etc/named.rfc1912.zone
```
zone "example.com" IN {

    type master;
    file "example.com.zone";
    allow-update { none; };
};

zone "123.168.200.in-addr.arpa" IN {
    type master;
    file "example.com.rev";
    allow-update { none; };
};
```

<br>

```
cp -p /var/named/named.localhost example.com.zone
```

<br>

/var/named/example.com.zone
```
$TTL 600
@   IN      SOA     ns.example.com. CyberSecurityHat.example.com.
    NS              ns.example.com.
    A               200.168.123.10
    MX 10   example.com.
ns  A               ns.200.168.123.10
www A               www.200.168.123.10
```

<br>

```
cp -p /var/named/example.com.zone /var/named/example.com.rev
```

<br>

/var/named/example.com.rev
```
$TTL 600
@   IN	    SOA     ns.example.com. CyberSecurityHat.example.com.
    NS              ns.example.com.
10  PTR             example.com.
10  PTR             ns.example.com.
10  PTR             www.example.com.
```