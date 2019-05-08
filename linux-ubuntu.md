##  linux \(ubuntu\)


### JDK
```
sudo apt install default-jdk              # version 2:1.11-71, or
sudo apt install openjdk-11-jdk-headless  # version 11.0.3+7-1ubuntu1
sudo apt install openjdk-8-jdk-headless   # version 8u212-b01-1
sudo apt install ecj                      # version 3.16.0-1
sudo apt install openjdk-12-jdk-headless  # version 12.0.1+12-1
sudo apt install openjdk-13-jdk-headless  # version 13~13-0ubunt1
```


### TOMCAT
```bash
sudo apt list
sudo apt search tomcat
sudo apt-get install tomcat8*
```
```bash
ls -al
total 20
drwxr-xr-x  5 root    root    4096  1월  1 00:00 .
drwxr-xr-x 63 root    root    4096  1월  1 00:00 ..
lrwxrwxrwx  1 root    root      12  1월  1 00:00 conf -> /etc/tomcat8
drwxr-xr-x  2 tomcat8 tomcat8 4096  1월  1 00:00 lib
lrwxrwxrwx  1 root    root      17  1월  1 00:00 logs -> ../../log/tomcat8
drwxr-xr-x  2 root    root    4096  1월  1 00:00 policy
drwxrwxr-x  3 tomcat8 tomcat8 4096  1월  1 00:00 webapps
lrwxrwxrwx  1 root    root      19  1월  1 00:00 work -> ../../cache/tomcat8
```



### Oracle(10g x86)
(https://oss.oracle.com/debian/dists/unstable/non-free/binary-i386/)
```bash
sudo apt-get install libc6-i386
wget -c http://oss.oracle.com/debian/dists/unstable/main/binary-i386/libaio_0.3.104-1_i386.deb http://oss.oracle.com/debian/dists/unstable/non-free/binary-i386/oracle-xe-universal_10.2.0.1-1.1_i386.deb
sudo apt-get install bc

sudo dpkg -i libaio_0.3.104-1_i386.deb

sudo dpkg -i oracle-xe-universal_10.2.0.1-1.1_i386.deb

sudo /etc/init.d/oracle-xe configure

Enter [YOUR DEFINED PASSWORD]
```

and edit your ~/.bashrc
```bash
ORACLE_HOME=/usr/lib/oracle/xe/app/oracle/product/10.2.0/server
PATH=$PATH:$ORACLE_HOME/bin
export ORACLE_HOME
export ORACLE_SID=XE
export PATH
```
go to http://127.0.0.1:8080/apex from your browser.
sqlplus sys/[YOUR DEFINED PASSWORD]
```sql
$ sqlplus /nolog
SQL*Plus: Release 11.2.0.1.0 Production on Wed Apr 1 11:51:29 2015

Copyright (c) 1982, 2009, Oracle.  All rights reserved. 


SQL> conn sys/ as sysdba
Enter password:
Connected.
 

SQL> startup
ORACLE instance started.

Total System Global Area  422670336 bytes
Fixed Size                  1336960 bytes
Variable Size             272632192 bytes
Database Buffers          142606336 bytes
Redo Buffers                6094848 bytes
Database mounted.
Database opened.

 

SQL> conn scott/tiger
Connected.

SQL> exit

SQL> conn system/password
Connected.

SQL> alter user HR account unlock ; 
SQL> alter user HR identified by $password ; 
SQL> exit
sqlplus HR/$password
SQL> SELECT table_name FROM user_tables;
SQL> SELECT * FROM regions ;
SQL> INSERT INTO REGIONS (REGION_ID, REGION_NAME) VALUES (666, 'Outer Mongolia') ;
SQL> COMMIT ;
```

### Oracle(11g x64)
```bash
$ unzip oracle*

$ cd Disk1

$ apt-get -y install alien libaio1 unixodbc

$ alien --scripts -d oracle*

$ cd /

$ mkdir /swap

$ dd if=/dev/zero of=/swap/swapfile bs=1024 count=2097152

$ cd /swap

$ mkswap swapfile

$ swapon swapfile

$ apt-get install bc
$ cd /download
$ cd Disk1
$ dpkg --install oracle*.deb
```
* listener 등록
```bash
$ cd /u01/app/oracle/product/11.2.0/xe/network/admin
$ nano listener.ora
```
```bash
SID_LIST_LISTENER =
  (SID_LIST =
    (SID_DESC =
      (SID_NAME = CLRExtProc)
      (ORACLE_HOME = /u01/app/oracle/product/11.2.0/xe)
      (PROGRAM = extproc)
    )
    (SID_DESC =
      (GLOBAL_DBNAME = XE)
      (ORACLE_HOME = /u01/app/oracle/product/11.2.0/xe)
      (SID_NAME = XE)
    )
  )

LISTENER =
  (DESCRIPTION_LIST =
    (DESCRIPTION =
      (ADDRESS = (PROTOCOL = IPC)(KEY = EXTPROC_FOR_XE))
      (ADDRESS = (PROTOCOL = TCP)(HOST = ip-172-500-5xx-22)($
    )
  )


DEFAULT_SERVICE_LISTENER = (XE)
(SID_DESC =
      (GLOBAL_DBNAME = XE)
      (ORACLE_HOME = /u01/app/oracle/product/11.2.0/xe)
      (SID_NAME = XE)
    )
```    

* $ /etc/init.d/oracle-xe configure
* netstat -nlpt
* cd /u01/app/oracle/product/11.2.0/xe/bin 
* . ./oracle_env.sh 
    ``` 
    sqlplus /nolog 
    ```
* conn sys as sysdba
