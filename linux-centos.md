# linux \(centos\)



### GUI

* yum group list
* yum group install "GNOME Desktop" 
* vi /etc/inittab 
  * 0 : halt\(종료\)
  * 1 : single mode\(복구\)
  * 2 : multi\_user\_mode\(네트워크X\) 
  * 3 : multi\_user\_mode\(네트워크O\) 
  * 4 : unused 사용하지 x 
  * 5 : graphical\_mode 
  * 6 : reboot\(재시작\)
* init &lt;level&gt;
* systemctl set-default graphical.target  \(systemctl set-default\)
* reboot

### add sudo

* groupadd sudo --system
* visudo  
  * %sudo ALL=\(ALL:ALL\) ALL
* add
  * usermod -aG sudo &lt;id&gt;
  * adduser &lt;id&gt; sudo



### Java

```bash
wget jdk-8u131-linux-x64.rpm
rpm -ivh jdk-8u131-linux-x64.rpm
alternatives --config java
```



### Tomcat

```bash
>yum list installed
>yum list | grep tomcat
>yum install -y tomcat*


>cd /usr/share/tomcat
>ls -al
drwxrwxr-x.   3 root tomcat   91  1월  1 00:00 .
drwxr-xr-x. 237 root root   8192  1월  1 00:00 ..
drwxr-xr-x.   2 root root     76  1월  1 00:00 bin
lrwxrwxrwx.   1 root tomcat   11  1월  1 00:00 conf -> /etc/tomcat
lrwxrwxrwx.   1 root tomcat   22  1월  1 00:00 lib -> /usr/share/java/tomcat
lrwxrwxrwx.   1 root tomcat   15  1월  1 00:00 logs -> /var/log/tomcat
lrwxrwxrwx.   1 root tomcat   22  1월  1 00:00 temp -> /var/cache/tomcat/temp
lrwxrwxrwx.   1 root tomcat   23  1월  1 00:00 webapps -> /var/lib/tomcat/webapps
lrwxrwxrwx.   1 root tomcat   22  1월  1 00:00 work -> /var/cache/tomcat/work
```



```text
$ firewall-cmd --permanent --add-port=8080/tcp 
$ firewall-cmd --reload
## 부팅시 실행
$ systemctl enable tomcat
## 서비스 시작
$ systemctl start tomcat
```













### VirtualBox additions



1. Install kernel include headers \(required by VBoxLinuxAdditions\).
   * RHEL: `sudo apt-get update && sudo apt-get install kernel-devel`
   * CentOS: `sudo yum update && sudo yum -y install kernel-headers kernel-devel`
2. Install Guest Additions \(this depends on the operating system\).
   * Ubuntu: `sudo apt-get -y install dkms build-essential linux-headers-$(uname -r) virtualbox-guest-additions-iso`

     If you can't find it, check by `aptitude search virtualbox`.

   * Debian: `sudo apt-get -y install build-essential module-assistant virtualbox-ose-guest-utils`

