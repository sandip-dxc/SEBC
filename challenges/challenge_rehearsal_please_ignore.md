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


<br><code>[base]</code></br>
<br><code>name=CentOS-$releasever - Base</code></br>
<br><code>mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=os&infra=$infra</code></br>
<br><code>#baseurl=http://mirror.centos.org/centos/$releasever/os/$basearch/</code></br>
<br><code>gpgcheck=1</code></br>
<br><code>gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7</code></br>

<br></br>












