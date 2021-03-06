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

<br>Installed Packages</br>
<br></br>
<br><code>[root@ip-172-31-13-124 yum.repos.d]# rpm -qa|grep cloudera</code></br>
<br></br>
<br><code>cloudera-manager-server-5.11.0-1.cm5110.p0.101.el7.x86_64</code></br>
<br><code>cloudera-manager-daemons-5.11.0-1.cm5110.p0.101.el7.x86_64</code></br>
<br></br>
<br><code>[root@ip-172-31-13-124 yum.repos.d]# rpm -qa|grep oracle</code></br>
<br></br>
<br><code>oracle-j2sdk1.7-1.7.0+update67-1.x86_64</code></br>


<br>Using the scm_prepare_database.sh</br>
<br></br>
<br><code>[root@ip-172-31-13-124 yum.repos.d]# /usr/share/cmf/schema/scm_prepare_database.sh mysql -v -u root -p scm scm scm</code></br>
<br><code>Enter database password:</code></br>
<br></br>

<br><code>JAVA_HOME=/usr/java/jdk1.7.0_67-cloudera</code></br>
<br><code>Verifying that we can write to /etc/cloudera-scm-server</code></br>
<br><code>Database type: mysql</code></br>
<br><code>Database user: root</code></br>
<br><code>Executing: /usr/java/jdk1.7.0_67-cloudera/bin/java -cp /usr/share/java/mysql-connector-java.jar:/usr/share/java/oracle-connector-java.jar:/usr/share/cmf/schema/../lib/*</code></br>
<br><code>com.cloudera.enterprise.dbutil.DbProvisioner --create -h localhost -u root -H localhost -U scm -d scm -t mysql</code></br>
<br><code>Creating SCM configuration file in /etc/cloudera-scm-server</code></br>
<br><code>Created db.properties file:</code></br>
        <br><code># Auto-generated by scm_prepare_database.sh on Thu May  4 20:10:54 EDT 2017</code></br>
        <br><code>#</code></br>
        <br><code># For information describing how to configure the Cloudera Manager Server</code></br>
        <br><code># to connect to databases, see the "Cloudera Manager Installation Guide."</code></br>
        <br><code>#</code></br>
        <br><code>com.cloudera.cmf.db.type=mysql</code></br>
        <br><code>com.cloudera.cmf.db.host=localhost</code></br>
        <br><code>com.cloudera.cmf.db.name=scm</code></br>
        <br><code>com.cloudera.cmf.db.user=scm</code></br>
        <br><code>com.cloudera.cmf.db.setupType=EXTERNAL</code></br>
        <br><code>com.cloudera.cmf.db.password=scm</code></br>
<br><code>Executing:  /usr/java/jdk1.7.0_67-cloudera/bin/java -cp /usr/share/java/mysql-connector-java.jar:/usr/share/java/oracle-connector-java.jar:/usr/share/cmf/schema/../lib/*</code></br> 
<br><code>com.cloudera.enterprise.dbutil.DbCommandExecutor /etc/cloudera-scm-server/db.properties com.cloudera.cmf.db.</code></br>
<br><code>[                          main] DbCommandExecutor              INFO  Successfully connected to database.</code></br>
<br><code>All done, your SCM database is configured correctly!</code></br>
<br></br>

<br>First line from Cloudera-scm-log</br>

<br><code>[root@ip-172-31-13-124 cloudera-scm-server]# head -1 cloudera-scm-server.log</code></br>
<br></br>
<br><code>2017-05-04 20:18:43,354 INFO main:com.cloudera.server.cmf.Main: Starting SCM Server. JVM Args: [-Dlog4j.configuration=file:/etc/cloudera-scm-server/log4j.properties, -Dfile.encoding=UTF-8, -Dcmf.root.logger=INFO,LOGFILE, -Dcmf.log.dir=/var/log/cloudera-scm-server, -Dcmf.log.file=cloudera-scm-server.log, -Dcmf.jetty.threshhold=WARN, -Dcmf.schema.dir=/usr/share/cmf/schema, -Djava.awt.headless=true, -Djava.net.preferIPv4Stack=true, -Dpython.home=/usr/share/cmf/python, -XX:+UseConcMarkSweepGC, -XX:+UseParNewGC, -XX:+HeapDumpOnOutOfMemoryError, -Xmx2G, -XX:MaxPermSize=256m, -XX:+HeapDumpOnOutOfMemoryError, -XX:HeapDumpPath=/tmp, -XX:OnOutOfMemoryError=kill -9 %p], Args: [], Version: 5.11.0 (#101 built by jenkins on 20170412-1255 git: 70cb1442626406432a6e7af5bdf206a384ca3f98)</code></br>

<br>line containing "Started Jetty Server"</br>
<br><code>[root@ip-172-31-13-124 cloudera-scm-server]# cat cloudera-scm-server.log|grep "Started Jetty server"</code></br>
<br></br>
<br><code>2017-05-04 20:20:08,329 INFO WebServerImpl:com.cloudera.server.cmf.WebServerImpl: Started Jetty server.</code></br>




<br>Displaying the content of db.properties</br>
<br></br>
<br><code>[root@ip-172-31-13-124 yum.repos.d]# cat /etc/cloudera-scm-server/db.properties</code></br>
<br></br>

<br><code># Auto-generated by scm_prepare_database.sh on Thu May  4 20:10:54 EDT 2017</code></br>
<br><code>#</code></br>
<br><code># For information describing how to configure the Cloudera Manager Server</code></br>
<br><code># to connect to databases, see the "Cloudera Manager Installation Guide."</code></br>
<br><code>#</code></br>
<br><code>com.cloudera.cmf.db.type=mysql</code></br>
<br><code>com.cloudera.cmf.db.host=localhost</code></br>
<br><code>com.cloudera.cmf.db.name=scm</code></br>
<br><code>com.cloudera.cmf.db.user=scm</code></br>
<br><code>com.cloudera.cmf.db.setupType=EXTERNAL</code></br>
<br><code>com.cloudera.cmf.db.password=scm</code></br>
<br><code>[root@ip-172-31-13-124 yum.repos.d]#</code></br>
<br></br>

<br>/************** END OF CHALLENGE # 2 ************/</br>