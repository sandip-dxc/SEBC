<br>The Cloud provider is AWS</br>

<br>Node List by Private IP and Name  </br>
<br>Node1: 172.31.13.124: ip-172-31-13-124.ap-southeast-2.compute.internal </br>
<br>Node2: 172.31.8.92: ip-172-31-8-92.ap-southeast-2.compute.internal </br>
<br>Node3: 172.31.7.151: ip-172-31-7-151.ap-southeast-2.compute.internal </br>
<br>Node4: 172.31.12.89: ip-172-31-12-89.ap-southeast-2.compute.internal </br>
<br>Node5: 172.31.9.140: ip-172-31-9-140.ap-southeast-2.compute.internal </br>

<br></br>
<br></br>

<br>Linux Release  </br>
<br><code>cat /etc/redhat-release  </code></br>
<br><code> Red Hat Enterprise Linux Server release 7.1 (Maipo) </code></br>

<br></br>
<br></br>

<br>Disk Capacity</br>
<br><code>df -h  </code></br>

<br><code>Filesystem      Size  Used Avail Use% Mounted on</code></br>
<br><code>/dev/xvda2       30G  867M   30G   3% /</code></br>
<br><code>devtmpfs        7.3G     0  7.3G   0% /dev</code></br>
<br><code>tmpfs           7.2G     0  7.2G   0% /dev/shm</code></br>
<br><code>tmpfs           7.2G   17M  7.2G   1% /run</code></br>
<br><code>tmpfs           7.2G     0  7.2G   0% /sys/fs/cgroup</code></br>

<br></br>
<br></br>

<br>yum repolist enabled</br>
<br><code>yum repolist enabled </code></br>
<br><code>[root@ip-172-31-13-124 ~]# yum repolist enabled</code></br>
<br><code>Loaded plugins: amazon-id, rhui-lb</code></br>
<br><code>rhui-REGION-client-config-server-7                                                                                        | 2.9 kB  00:00:00</code></br>
<br><code>rhui-REGION-rhel-server-releases                                                                                          | 3.5 kB  00:00:00</code></br>
<br><code>rhui-REGION-rhel-server-rh-common                                                                                         | 3.8 kB  00:00:00</code></br>
<br><code>(1/7): rhui-REGION-rhel-server-rh-common/7Server/x86_64/group                                                             |  104 B  00:00:00</code></br>
<br><code>(2/7): rhui-REGION-rhel-server-releases/7Server/x86_64/group                                                              | 701 kB  00:00:00</code></br>
<br><code>(3/7): rhui-REGION-rhel-server-releases/7Server/x86_64/updateinfo                                                         | 1.9 MB  00:00:00</code></br>
<br><code>(4/7): rhui-REGION-client-config-server-7/x86_64/primary_db                                                               | 5.4 kB  00:00:00</code></br>
<br><code>(5/7): rhui-REGION-rhel-server-rh-common/7Server/x86_64/updateinfo                                                        |  33 kB  00:00:00</code></br>
<br><code>(6/7): rhui-REGION-rhel-server-rh-common/7Server/x86_64/primary_db                                                        | 118 kB  00:00:00</code></br>
<br><code>(7/7): rhui-REGION-rhel-server-releases/7Server/x86_64/primary_db                                                         |  35 MB  00:00:00</code></br>
<br><code>repo id                                                       repo name                                                                    status</code></br>
<br><code>rhui-REGION-client-config-server-7/x86_64                     Red Hat Update Infrastructure 2.0 Client Configuration Server 7                   6</code></br>
<br><code>rhui-REGION-rhel-server-releases/7Server/x86_64               Red Hat Enterprise Linux Server 7 (RPMs)                                     14,277</code></br>
<br><code>rhui-REGION-rhel-server-rh-common/7Server/x86_64              Red Hat Enterprise Linux Server 7 RH Common (RPMs)                              228</code></br>
<br><code>repolist: 14,511</code></br>

<br></br>
<br></br>


<br>Group and user add - Executed as a script</br>

<br><code>groupadd kiwis -g 9980;</code></br>
<br><code>groupadd aussies -g 9990;</code></br>
<br><code>useradd -G aussies -u 2300 -p $(openssl passwd -1 welcome123) -s /bin/bash -m -d /home/cate -c "cate, Hadoop Aussie" cate;</code></br>
<br><code>useradd -G kiwis -u 2900 -p $(openssl passwd -1 welcome123) -s /bin/bash -m -d /home/jemaine -c "jemaine, Hadoop Kiwi" jemaine;</code></br>

<br></br>

<br>Listing of users and groups</br>


<br><code>[root@ip-172-31-13-124 ~]# grep 'kiwis\|aussies' /etc/group</code></br>
<br><code>kiwis:x:9980:jemaine</code></br>
<br><code>aussies:x:9990:cate</code></br>




<br><code>[root@ip-172-31-13-124 ~]# grep 'cate\|jemaine' /etc/passwd</code></br>
<br><code>cate:x:2300:2300:cate, Hadoop Aussie:/home/cate:/bin/bash</code></br>
<br><code>jemaine:x:2900:2900:jemaine, Hadoop Kiwi:/home/jemaine:/bin/bash</code></br>


<br></br>

<br>/************** END OF ISSUE # 1 ***************/</br>
