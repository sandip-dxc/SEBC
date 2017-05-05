



<br>/************** START OF CHALLENGE # 2 ************/</br>

<br></br>
<br><code>[root@ip-172-31-13-124 yum.repos.d]# ls /etc/yum.repos.d</code></br>
<br><code>cm.repo  redhat.repo  redhat-rhui-client-config.repo  redhat-rhui.repo  rhui-load-balancers.conf</code></br>
<br></br>

<br><code>[root@ip-172-31-13-124 yum.repos.d]# cat cm.repo</code></br>
<br></br>
<br><code>[cloudera-manager]</code></br>
<br><code># Packages for Cloudera Manager, Version 5, on RedHat or CentOS 7 x86_64</code></br>
<br><code>name=Cloudera Manager</code></br>
<br><code>baseurl=https://archive.cloudera.com/cm5/redhat/7/x86_64/cm/5/</code></br>
<br><code>gpgkey =https://archive.cloudera.com/cm5/redhat/7/x86_64/cm/RPM-GPG-KEY-cloudera</code></br>
<br><code>gpgcheck = 1</code></br>
<br></br>
