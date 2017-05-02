
1. Swappiness
2. Mount 
3. file system
4. Huge page disable
5. Network interface config
6. Forward and Reverse Lookups (both private and public IP/hostname)
7. NSCP & NTPD - Currently not working
8. All hosts are on RHEL 7.2
[root@ip-172-31-0-192 transparent_hugepage]# cat /etc/redhat-release
Red Hat Enterprise Linux Server release 7.2 (Maipo)



/** Host # 1 **/



[root@ip-172-31-1-239 vm]# ip addr|grep inet
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host
    inet 172.31.1.239/20 brd 172.31.15.255 scope global dynamic eth0
    inet6 fe80::76:55ff:fe2f:a7bb/64 scope link
[root@ip-172-31-1-239 vm	]# sysctl -a | grep vm.swappiness
vm.swappiness = 30
[root@ip-172-31-1-239 vm]# sysctl -w vm.swappiness=1
vm.swappiness = 1
[root@ip-172-31-1-239 vm]# sysctl -a | grep vm.swappiness
vm.swappiness = 1


[root@ip-172-31-1-239 vm]# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda2       30G  1.2G   29G   4% /
devtmpfs        7.3G     0  7.3G   0% /dev
tmpfs           7.2G     0  7.2G   0% /dev/shm
tmpfs           7.2G   17M  7.2G   1% /run
tmpfs           7.2G     0  7.2G   0% /sys/fs/cgroup
tmpfs           1.5G     0  1.5G   0% /run/user/1000




[root@ip-172-31-1-239 vm]# parted -l
Model: Xen Virtual Block Device (xvd)
Disk /dev/xvda: 32.2GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2097kB  1049kB                     bios_grub
 2      2097kB  32.2GB  32.2GB  xfs

 
[root@ip-172-31-1-239 transparent_hugepage]# echo never > defrag
[root@ip-172-31-1-239 transparent_hugepage]# echo never > enabled
[root@ip-172-31-1-239 transparent_hugepage]# pwd
/sys/kernel/mm/transparent_hugepage
[root@ip-172-31-1-239 transparent_hugepage]# cat defrag
always madvise [never]
[root@ip-172-31-1-239 transparent_hugepage]# cat enabled
always madvise [never]


[root@ip-172-31-1-239 network-scripts]# cat /etc/sysconfig/network-scripts/ifcfg-eth0
DEVICE="eth0"
BOOTPROTO="dhcp"
ONBOOT="yes"
TYPE="Ethernet"
USERCTL="yes"
PEERDNS="yes"
IPV6INIT="no"


[root@ip-172-31-1-239 network-scripts]# getent hosts 172.31.1.239
172.31.1.239    ip-172-31-1-239.ap-southeast-2.compute.internal
[root@ip-172-31-1-239 network-scripts]# getent hosts ip-172-31-1-239.ap-southeast-2.compute.internal
172.31.1.239    ip-172-31-1-239.ap-southeast-2.compute.internal
[root@ip-172-31-1-239 network-scripts]# getent hosts 13.55.133.65
13.55.133.65    ec2-13-55-133-65.ap-southeast-2.compute.amazonaws.com
[root@ip-172-31-1-239 network-scripts]# getent hosts ec2-13-55-133-65.ap-southeast-2.compute.amazonaws.com
172.31.1.239    ec2-13-55-133-65.ap-southeast-2.compute.amazonaws.com



/***************/



/** Host # 2 **/

[root@ip-172-31-1-56 ~]# ip addr|grep inet
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host
    inet 172.31.1.56/20 brd 172.31.15.255 scope global dynamic eth0
    inet6 fe80::c5:3ff:fe45:afb/64 scope link
[root@ip-172-31-1-56 ~]# sysctl -a | grep vm.swappiness
vm.swappiness = 30
[root@ip-172-31-1-56 ~]# sysctl -w vm.swappiness=1
vm.swappiness = 1
[root@ip-172-31-1-56 ~]# sysctl -a | grep vm.swappiness
vm.swappiness = 1
[root@ip-172-31-1-56 ~]#


[root@ip-172-31-1-56 ~]# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda2       30G  943M   30G   4% /
devtmpfs        7.3G     0  7.3G   0% /dev
tmpfs           7.2G     0  7.2G   0% /dev/shm
tmpfs           7.2G   17M  7.2G   1% /run
tmpfs           7.2G     0  7.2G   0% /sys/fs/cgroup
tmpfs           1.5G     0  1.5G   0% /run/user/1000



[root@ip-172-31-1-56 ~]# parted -l
Model: Xen Virtual Block Device (xvd)
Disk /dev/xvda: 32.2GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2097kB  1049kB                     bios_grub
 2      2097kB  32.2GB  32.2GB  xfs

 
 
 [root@ip-172-31-1-56 ~]# cd /sys/kernel/mm/transparent_hugepage
[root@ip-172-31-1-56 transparent_hugepage]# echo never > defrag
[root@ip-172-31-1-56 transparent_hugepage]# echo never > enabled
[root@ip-172-31-1-56 transparent_hugepage]# cat defrag
always madvise [never]
[root@ip-172-31-1-56 transparent_hugepage]# cat enabled
always madvise [never]
[root@ip-172-31-1-56 transparent_hugepage]# pwd
/sys/kernel/mm/transparent_hugepage



[root@ip-172-31-1-56 transparent_hugepage]# cat /etc/sysconfig/network-scripts/ifcfg-eth0
DEVICE="eth0"
BOOTPROTO="dhcp"
ONBOOT="yes"
TYPE="Ethernet"
USERCTL="yes"
PEERDNS="yes"
IPV6INIT="no"



[root@ip-172-31-1-56 transparent_hugepage]# getent hosts 172.31.1.56
172.31.1.56     ip-172-31-1-56.ap-southeast-2.compute.internal
[root@ip-172-31-1-56 transparent_hugepage]# getent hosts ip-172-31-1-56.ap-southeast-2.compute.internal
172.31.1.56     ip-172-31-1-56.ap-southeast-2.compute.internal
[root@ip-172-31-1-56 transparent_hugepage]# getent hosts 52.64.205.110
52.64.205.110   ec2-52-64-205-110.ap-southeast-2.compute.amazonaws.com
[root@ip-172-31-1-56 transparent_hugepage]# getent hosts ec2-52-64-205-110.ap-southeast-2.compute.amazonaws.com
172.31.1.56     ec2-52-64-205-110.ap-southeast-2.compute.amazonaws.com


 
 
/***************/



/** Host # 3 **/

[root@ip-172-31-13-20 ~]# ip addr|grep inet
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host
    inet 172.31.13.20/20 brd 172.31.15.255 scope global dynamic eth0
    inet6 fe80::f0:cfff:fea2:ebd7/64 scope link
[root@ip-172-31-13-20 ~]# sysctl -a | grep vm.swappiness
vm.swappiness = 30
[root@ip-172-31-13-20 ~]# sysctl -w vm.swappiness=1
vm.swappiness = 1
[root@ip-172-31-13-20 ~]# sysctl -a | grep vm.swappiness
vm.swappiness = 1
[root@ip-172-31-13-20 ~]#

[root@ip-172-31-13-20 ~]# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda2       30G  942M   30G   4% /
devtmpfs        7.3G     0  7.3G   0% /dev
tmpfs           7.2G     0  7.2G   0% /dev/shm
tmpfs           7.2G   17M  7.2G   1% /run
tmpfs           7.2G     0  7.2G   0% /sys/fs/cgroup
tmpfs           1.5G     0  1.5G   0% /run/user/1000


[root@ip-172-31-13-20 ~]# parted -l
Model: Xen Virtual Block Device (xvd)
Disk /dev/xvda: 32.2GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2097kB  1049kB                     bios_grub
 2      2097kB  32.2GB  32.2GB  xfs


[root@ip-172-31-13-20 ~]#
[root@ip-172-31-13-20 ~]# cd /sys/kernel/mm/transparent_hugepage
[root@ip-172-31-13-20 transparent_hugepage]# pwd
/sys/kernel/mm/transparent_hugepage
[root@ip-172-31-13-20 transparent_hugepage]# echo never > defrag
[root@ip-172-31-13-20 transparent_hugepage]# echo never > enabled
[root@ip-172-31-13-20 transparent_hugepage]# cat defrag
always madvise [never]
[root@ip-172-31-13-20 transparent_hugepage]# cat enabled
always madvise [never]


[root@ip-172-31-13-20 transparent_hugepage]# cat /etc/sysconfig/network-scripts/ifcfg-eth0
DEVICE="eth0"
BOOTPROTO="dhcp"
ONBOOT="yes"
TYPE="Ethernet"
USERCTL="yes"
PEERDNS="yes"
IPV6INIT="no"


[root@ip-172-31-13-20 transparent_hugepage]# getent hosts 172.31.13.20
172.31.13.20    ip-172-31-13-20.ap-southeast-2.compute.internal
[root@ip-172-31-13-20 transparent_hugepage]# getent hosts ip-172-31-13-20.ap-southeast-2.compute.internal
172.31.13.20    ip-172-31-13-20.ap-southeast-2.compute.internal
[root@ip-172-31-13-20 transparent_hugepage]# getent hosts 52.63.41.156
52.63.41.156    ec2-52-63-41-156.ap-southeast-2.compute.amazonaws.com
[root@ip-172-31-13-20 transparent_hugepage]# getent hosts ec2-52-63-41-156.ap-southeast-2.compute.amazonaws.com
172.31.13.20    ec2-52-63-41-156.ap-southeast-2.compute.amazonaws.com


/***************/



/** Host # 4 **/

[root@ip-172-31-9-249 ~]# ip addr|grep inet
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host
    inet 172.31.9.249/20 brd 172.31.15.255 scope global dynamic eth0
    inet6 fe80::cb:22ff:fe15:3591/64 scope link
[root@ip-172-31-9-249 ~]# sysctl -a | grep vm.swappiness
vm.swappiness = 30
[root@ip-172-31-9-249 ~]# sysctl -w vm.swappiness=1
vm.swappiness = 1
[root@ip-172-31-9-249 ~]# sysctl -a | grep vm.swappiness
vm.swappiness = 1
[root@ip-172-31-9-249 ~]#

[root@ip-172-31-9-249 ~]# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda2       30G  942M   30G   4% /
devtmpfs        7.3G     0  7.3G   0% /dev
tmpfs           7.2G     0  7.2G   0% /dev/shm
tmpfs           7.2G   17M  7.2G   1% /run
tmpfs           7.2G     0  7.2G   0% /sys/fs/cgroup
tmpfs           1.5G     0  1.5G   0% /run/user/1000


[root@ip-172-31-9-249 ~]# parted -l
Model: Xen Virtual Block Device (xvd)
Disk /dev/xvda: 32.2GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2097kB  1049kB                     bios_grub
 2      2097kB  32.2GB  32.2GB  xfs


[root@ip-172-31-9-249 ~]# cd /sys/kernel/mm/transparent_hugepage
[root@ip-172-31-9-249 transparent_hugepage]# pwd
/sys/kernel/mm/transparent_hugepage
[root@ip-172-31-9-249 transparent_hugepage]# echo never > defrag
[root@ip-172-31-9-249 transparent_hugepage]# echo never > enabled
[root@ip-172-31-9-249 transparent_hugepage]# cat defrag
always madvise [never]
[root@ip-172-31-9-249 transparent_hugepage]# cat enabled
always madvise [never]


[root@ip-172-31-9-249 transparent_hugepage]# cat /etc/sysconfig/network-scripts/ifcfg-eth0
DEVICE="eth0"
BOOTPROTO="dhcp"
ONBOOT="yes"
TYPE="Ethernet"
USERCTL="yes"
PEERDNS="yes"
IPV6INIT="no"



[root@ip-172-31-9-249 transparent_hugepage]# getent hosts 172.31.9.249
172.31.9.249    ip-172-31-9-249.ap-southeast-2.compute.internal
[root@ip-172-31-9-249 transparent_hugepage]# getent hosts ip-172-31-9-249.ap-southeast-2.compute.internal
172.31.9.249    ip-172-31-9-249.ap-southeast-2.compute.internal
[root@ip-172-31-9-249 transparent_hugepage]# getent hosts 52.63.187.42
52.63.187.42    ec2-52-63-187-42.ap-southeast-2.compute.amazonaws.com
[root@ip-172-31-9-249 transparent_hugepage]# getent hosts ec2-52-63-187-42.ap-southeast-2.compute.amazonaws.com
172.31.9.249    ec2-52-63-187-42.ap-southeast-2.compute.amazonaws.com


/***************/




/** Host # 5 **/

[root@ip-172-31-0-192 ~]# ip addr|grep inet
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host
    inet 172.31.0.192/20 brd 172.31.15.255 scope global dynamic eth0
    inet6 fe80::c3:17ff:feca:5837/64 scope link
[root@ip-172-31-0-192 ~]# sysctl -a | grep vm.swappiness
vm.swappiness = 30
[root@ip-172-31-0-192 ~]# sysctl -w vm.swappiness=1
vm.swappiness = 1
[root@ip-172-31-0-192 ~]# sysctl -a | grep vm.swappiness
vm.swappiness = 1


[root@ip-172-31-0-192 ~]# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda2       30G  942M   30G   4% /
devtmpfs        7.3G     0  7.3G   0% /dev
tmpfs           7.2G     0  7.2G   0% /dev/shm
tmpfs           7.2G   17M  7.2G   1% /run
tmpfs           7.2G     0  7.2G   0% /sys/fs/cgroup
tmpfs           1.5G     0  1.5G   0% /run/user/1000


[root@ip-172-31-0-192 ~]# parted -l
Model: Xen Virtual Block Device (xvd)
Disk /dev/xvda: 32.2GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2097kB  1049kB                     bios_grub
 2      2097kB  32.2GB  32.2GB  xfs


[root@ip-172-31-0-192 ~]# cd /sys/kernel/mm/transparent_hugepage
[root@ip-172-31-0-192 transparent_hugepage]# pwd
/sys/kernel/mm/transparent_hugepage
[root@ip-172-31-0-192 transparent_hugepage]# echo never > defrag
[root@ip-172-31-0-192 transparent_hugepage]# echo never > enabled
[root@ip-172-31-0-192 transparent_hugepage]# cat defrag
always madvise [never]
[root@ip-172-31-0-192 transparent_hugepage]# cat enabled
always madvise [never]




[root@ip-172-31-0-192 transparent_hugepage]# cat /etc/sysconfig/network-scripts/ifcfg-eth0
DEVICE="eth0"
BOOTPROTO="dhcp"
ONBOOT="yes"
TYPE="Ethernet"
USERCTL="yes"
PEERDNS="yes"
IPV6INIT="no"



[root@ip-172-31-0-192 transparent_hugepage]# getent hosts 172.31.0.192
172.31.0.192    ip-172-31-0-192.ap-southeast-2.compute.internal
[root@ip-172-31-0-192 transparent_hugepage]# getent hosts ip-172-31-0-192.ap-southeast-2.compute.internal
172.31.0.192    ip-172-31-0-192.ap-southeast-2.compute.internal
[root@ip-172-31-0-192 transparent_hugepage]# getent hosts 13.55.225.206
13.55.225.206   ec2-13-55-225-206.ap-southeast-2.compute.amazonaws.com
[root@ip-172-31-0-192 transparent_hugepage]# getent hosts ec2-13-55-225-206.ap-southeast-2.compute.amazonaws.com
172.31.0.192    ec2-13-55-225-206.ap-southeast-2.compute.amazonaws.com


/***************/




This is all good, but why change the swappiness in the first place ?

Basically, reduce the disk I/O. Plenty of references on the net, one good one is:
https://lonesysadmin.net/2013/12/11/adjust-vm-swappiness-avoid-unneeded-disk-io/


File System Information:
Refer Redhat solution https://access.redhat.com/solutions/1532 for the different types of file systems

https://access.redhat.com/solutions/1980673 : How XFS differs from EXt in terms of reserve space. We have confirmed above that AWS have assigned XFS file syste by default and hence no reserve space is needed
