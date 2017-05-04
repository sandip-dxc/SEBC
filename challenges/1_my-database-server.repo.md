<br>/************** START OF CHALLENGE # 1 ************/</br>

<br>Yum Repository</br>

<br><code>[root@ip-172-31-13-124 ~]# yum list all|grep mariadb-server</code></br>
<br></br>
<br><code>mariadb-server.x86_64       1:5.5.52-1.el7      rhui-REGION-rhel-server-releases</code></br>
<br><code>[root@ip-172-31-13-124 ~]#</code></br>
<br>==============================================</br>

<br><code>[rhui-REGION-rhel-server-releases]</code></br>
<br><code>name=Red Hat Enterprise Linux Server 7 (RPMs)</code></br>
<br><code>mirrorlist=https://rhui2-cds01.REGION.aws.ce.redhat.com/pulp/mirror/content/dist/rhel/rhui/server/7/$releasever/$basearch/os</code></br>
<br><code>enabled=1</code></br>
<br><code>gpgcheck=1</code></br>
<br><code>gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release</code></br>
<br><code>sslverify=1</code></br>
<br><code>sslclientkey=/etc/pki/rhui/content-rhel7.key</code></br>
<br><code>sslclientcert=/etc/pki/rhui/product/content-rhel7.crt</code></br>
<br><code>sslcacert=/etc/pki/rhui/cdn.redhat.com-chain.crt</code></br>


<br> command for DB version </br>
<br><code>[root@ip-172-31-13-124 yum.repos.d]# rpm -qa|grep maria</code></br>
<br><code>mariadb-libs-5.5.52-1.el7.x86_64</code></br>
<br><code>mariadb-server-5.5.52-1.el7.x86_64</code></br>
<br><code>mariadb-5.5.52-1.el7.x86_64</code></br>

<br> Hostname of MariaDB server </br>

<br><code>[root@ip-172-31-13-124 yum.repos.d]# hostname</code></br>
<br><code>ip-172-31-13-124.ap-southeast-2.compute.internal</code></br>


<br> command and output for DB version installed </br>
<br><code>[root@ip-172-31-13-124 yum.repos.d]# rpm -qa|grep maria</code></br>
<br><code>mariadb-libs-5.5.52-1.el7.x86_64</code></br>
<br><code>mariadb-server-5.5.52-1.el7.x86_64</code></br>
<br><code>mariadb-5.5.52-1.el7.x86_64</code></br>

<br> command and output for listing the Databases created  </br>

<br>Please refer to 2_db_server.png for a screenshot of that command annd output</br>



<br>/************** END OF CHALLENGE # 1 ***************/</br>