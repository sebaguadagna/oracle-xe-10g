sebaguadagna/oracle-xe-10g 
====================

* Oracle Express Edition 10g Release 2 (10.2.0.1) 32-bit on Debian 8.0 Jessie.
* Forked from dragonbest520/oracle-xe-10g

**The default characterset is WE8ISO8859P1 and timezone is America/Montevideo.**


### Installation
Last release version-1.4
Replace tagname with release name
```
docker pull sebastianguadagna/ora10gxe:tagname
```


Run with 22, 1521, 8080 ports opened and volume mounted:
```
docker run --name oracle10g -d -p 49160:22 -p 1521:1521 -p 49162:8080 --mount source=oracle_xe_10g_vol,target=/usr/lib/oracle -e ORACLE_ALLOW_REMOTE=true --restart=always sebastianguadagna/ora10gxe:version-1.4
```

The volume path on server is /var/lib/docker/volumes/oracle_xe_10g_vol

If the container restart or redeployed, the data is still in the volume. 

Connect database with following setting:
```
hostname: localhost
port: 1521
sid: xe
username: system
password: oracle
```

For example, connect to database with sqlplus:
```
sqlplus system/oracle@localhost:1521/xe
```

Password for SYS & SYSTEM
```
oracle
```

Login by SSH
```
ssh root@localhost -p 49160
password: admin
```

Login to web administrator on a browser:
```
http://localhost:49162/apex
```
