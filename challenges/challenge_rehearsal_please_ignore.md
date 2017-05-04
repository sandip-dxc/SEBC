<br>The Cloud provider is AWS</br>

<br>Node List by Private IP and Name  </br>
<br>Node1:  </br>
<br>Node2:  </br>
<br>Node3:  </br>
<br>Node4:  </br>
<br>Node5:  </br>

<br></br>
<br></br>

<br>Linux Release  </br>
<br><code>cat /etc/redhat-release  </code></br>
<br><code> [OUTPUT]  </code></br>


<br></br>
<br></br>

<br>Disk Capacity</br>
<br><code>df -h  </code></br>
<br><code>Filesystem      Size  Used Avail Use% Mounted on</code></br>
<br><code>/dev/xvda2       30G  942M   30G   4% /</code></br>
<br><code>devtmpfs        7.3G     0  7.3G   0% /dev</code></br>
<br><code>tmpfs           7.2G     0  7.2G   0% /dev/shm</code></br>
<br><code>tmpfs           7.2G   17M  7.2G   1% /run</code></br>
<br><code>tmpfs           7.2G     0  7.2G   0% /sys/fs/cgroup</code></br>
<br><code>tmpfs           1.5G     0  1.5G   0% /run/user/1000</code></br>

<br></br>
<br></br>

<br>yum repolist enabled</br>
<br><code>yum repolist enabled </code></br>
<br><code> [OUTPUT]  </code></br>

<br></br>
<br></br>




<br>Group and user add - Executed as a script</br>

<br><code>groupadd barca -g 9980;</code></br>
<br><code>groupadd merengues -g 9990;</code></br>
<br><code>useradd -G merengues -u 2010 -p $(openssl passwd -1 welcome123) -s /bin/bash -m -d /home/neymar -c "Neymar Jr, Hadoop Administrator" neymar;</code></br>
<br><code>useradd -G barca -u 2016 -p $(openssl passwd -1 welcome123) -s /bin/bash -m -d /home/neymar -c "Ronaldo Cristiano, Hadoop Administrator" ronaldo;</code></br>

<br></br>

<br>Listing of users and groups</br>
<br><code>grep 'merengues\|barca' /etc/group;</code></br>
<br><code>grep 'neymar\|ronaldo' /etc/passwd;</code></br>

<br>Output</br>
<br><code> [OUTPUT]  </code></br>

<br></br>

<br>/************** END OF ISSUE # 1 ***************/</br>

<br>/************** START OF CHALLENGE # 1 ************/</br>

<br>Yum Repository</br>
<br></br>
<br><code>[base]</code></br>
<br><code>name=CentOS-$releasever - Base</code></br>
<br><code>mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=os&infra=$infra</code></br>
<br><code>#baseurl=http://mirror.centos.org/centos/$releasever/os/$basearch/</code></br>
<br><code>gpgcheck=1</code></br>
<br><code>gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7</code></br>

<br></br>

<br>Transfer Files from Local PC to AWS - Execute on DOS prompt</br>
<br></br>
<br><code>pscp -i sandip_dxc.ppk mysql-connector-java-5.1.42.tar.gz centos@52.65.138.83:/tmp</code></br>
<br><code>pscp -i sandip_dxc.ppk mysql-connector-java-5.1.42.tar.gz centos@52.65.49.88:/tmp</code></br>
<br><code>pscp -i sandip_dxc.ppk mysql-connector-java-5.1.42.tar.gz centos@52.62.72.114:/tmp</code></br>
<br><code>pscp -i sandip_dxc.ppk mysql-connector-java-5.1.42.tar.gz centos@13.55.15.70:/tmp</code></br>
<br><code>pscp -i sandip_dxc.ppk mysql-connector-java-5.1.42.tar.gz centos@52.65.118.198:/tmp</code></br>
<br></br>

<br>Unzip and copy the driver on all nodes</br>
<br></br>
<br><code>cd /tmp;</code></br>
<br><code>tar zxvf mysql-connector-java-5.1.42.tar.gz;</code></br>
<br><code>mkdir /usr/share/java;</code></br>
<br><code>cp /tmp/mysql-connector-java-5.1.42/mysql-connector-java-5.1.42-bin.jar /usr/share/java/mysql-connector-java.jar;</code></br>
<br><code>mkdir /var/lib/oozie;</code></br>
<br><code>cp /tmp/mysql-connector-java-5.1.42/mysql-connector-java-5.1.42-bin.jar /var/lib/oozie/mysql-connector-java.jar;</code></br>
<br></br>

<br>Execute mysql_secure_installation and start services</br>
<br><code>/usr/bin/mysql_secure_installation</code></br>
<br><code>systemctl start mariadb</code></br>
<br><code>systemctl status mariadb</code></br>
<br><code>create database amon DEFAULT CHARACTER SET utf8;</code></br>
<br><code>grant all on amon.* TO 'amon'@'%' IDENTIFIED BY 'amon';</code></br>
<br><code>create database rman DEFAULT CHARACTER SET utf8;</code></br>
<br><code>grant all on rman.* TO 'rman'@'%' IDENTIFIED BY 'rman';</code></br>
<br><code>create database hive DEFAULT CHARACTER SET utf8;</code></br>
<br><code>grant all on hive.* TO 'hive'@'%' IDENTIFIED BY 'hive';</code></br>
<br><code>create database sentry DEFAULT CHARACTER SET utf8;</code></br>
<br><code>grant all on sentry.* TO 'sentry'@'%' IDENTIFIED BY 'sentry';</code></br>
<br><code>create database nav DEFAULT CHARACTER SET utf8;</code></br>
<br><code>grant all on nav.* TO 'nav'@'%' IDENTIFIED BY 'nav';</code></br>
<br><code>create database navms DEFAULT CHARACTER SET utf8;</code></br>
<br><code>grant all on navms.* TO 'navms'@'%' IDENTIFIED BY 'navms';</code></br>
<br><code>create database hue default character set utf8 default collate utf8_general_ci;</code></br>
<br><code>grant all on hue.* to 'hue'@'%' identified by 'hue';</code></br>
<br><code>create database oozie;</code></br>
<br><code>grant all privileges on oozie.* to 'oozie'@'%' identified by 'oozie';</code></br>
<br></br>

<br>Hostname</br>
<br><code> [OUTPUT]  </code></br>
<br>Version of MariaDB installed</br>
<br><code> rpm -qa|grep mariadb   </code></br>
<br><code> [OUTPUT]  </code></br>
<br>List of databases</br>
<br><code> mysql -u root -p  </code></br>
<br><code> select * from information_schema.schemata;  </code></br>
<br><code> [OUTPUT]  </code></br>


<br>/************** END OF CHALLENGE # 1 ***************/</br>

<br>/************** START OF CHALLENGE # 2 ************/</br>




