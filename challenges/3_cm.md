<br>/************** END OF CHALLENGE # 1 ***************/</br>


<br>Refer to 3_CM_CDH_Version_Cluster_name_info.png for the version of CM, CDH and name of the cluster as per my github handle</br>
<br></br>
<br>Output of HDFS directory listing under /user</br>
<br></br>

<br><code>-bash-4.2$ hdfs dfs -ls /user</code></br>
<br><code>Found 7 items</code></br>
<br><code>drwxr-xr-x   - hdfs   supergroup          0 2017-05-04 21:34 /user/cate</code></br>
<br><code>drwxrwxrwx   - mapred hadoop              0 2017-05-04 21:21 /user/history</code></br>
<br><code>drwxrwxr-t   - hive   hive                0 2017-05-04 21:25 /user/hive</code></br>
<br><code>drwxrwxr-x   - hue    hue                 0 2017-05-04 21:26 /user/hue</code></br>
<br><code>drwxrwxr-x   - impala impala              0 2017-05-04 21:26 /user/impala</code></br>
<br><code>drwxr-xr-x   - hdfs   supergroup          0 2017-05-04 21:35 /user/jemaine</code></br>
<br><code>drwxrwxr-x   - oozie  oozie               0 2017-05-04 21:26 /user/oozie</code></br>

<br></br>

<br>output of CM API call ../api/v14/hosts</br>

{
  "items" : [ {
    "hostId" : "24ccf266-2333-457b-a49d-94ff9e405c8a",
    "ipAddress" : "172.31.12.89",
    "hostname" : "ip-172-31-12-89.ap-southeast-2.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-13-124.ap-southeast-2.compute.internal:7180/cmf/hostRedirect/24ccf266-2333-457b-a49d-94ff9e405c8a",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15332917248
  }, {
    "hostId" : "635fc6a4-ccf6-4ab0-a500-d0c5b6626deb",
    "ipAddress" : "172.31.13.124",
    "hostname" : "ip-172-31-13-124.ap-southeast-2.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-13-124.ap-southeast-2.compute.internal:7180/cmf/hostRedirect/635fc6a4-ccf6-4ab0-a500-d0c5b6626deb",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15332917248
  }, {
    "hostId" : "e1eacefe-6873-440e-806f-11b0fde1e8cb",
    "ipAddress" : "172.31.7.151",
    "hostname" : "ip-172-31-7-151.ap-southeast-2.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-13-124.ap-southeast-2.compute.internal:7180/cmf/hostRedirect/e1eacefe-6873-440e-806f-11b0fde1e8cb",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15332917248
  }, {
    "hostId" : "860dbb1c-90c5-4883-bef5-6605eb15bd24",
    "ipAddress" : "172.31.8.92",
    "hostname" : "ip-172-31-8-92.ap-southeast-2.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-13-124.ap-southeast-2.compute.internal:7180/cmf/hostRedirect/860dbb1c-90c5-4883-bef5-6605eb15bd24",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15332917248
  }, {
    "hostId" : "e0a32294-3dfe-47b0-a1d0-fb378b2d087d",
    "ipAddress" : "172.31.9.140",
    "hostname" : "ip-172-31-9-140.ap-southeast-2.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-13-124.ap-southeast-2.compute.internal:7180/cmf/hostRedirect/e0a32294-3dfe-47b0-a1d0-fb378b2d087d",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15332917248
  } ]
}

<br></br>
<br>Output of CM API call ../api/v6/clusters/<githubName>/services </br>
{
  "items" : [ {
    "name" : "hive",
    "type" : "HIVE",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://ip-172-31-13-124.ap-southeast-2.compute.internal:7180/cmf/serviceRedirect/hive",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "HIVE_HIVEMETASTORES_HEALTHY",
      "summary" : "GOOD"
    }, {
      "name" : "HIVE_HIVESERVER2S_HEALTHY",
      "summary" : "GOOD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "Hive"
  }, {
    "name" : "zookeeper",
    "type" : "ZOOKEEPER",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://ip-172-31-13-124.ap-southeast-2.compute.internal:7180/cmf/serviceRedirect/zookeeper",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "ZOOKEEPER_CANARY_HEALTH",
      "summary" : "GOOD"
    }, {
      "name" : "ZOOKEEPER_SERVERS_HEALTHY",
      "summary" : "GOOD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "ZooKeeper"
  }, {
    "name" : "hue",
    "type" : "HUE",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://ip-172-31-13-124.ap-southeast-2.compute.internal:7180/cmf/serviceRedirect/hue",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "HUE_HUE_SERVERS_HEALTHY",
      "summary" : "GOOD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "Hue"
  }, {
    "name" : "oozie",
    "type" : "OOZIE",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://ip-172-31-13-124.ap-southeast-2.compute.internal:7180/cmf/serviceRedirect/oozie",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "OOZIE_OOZIE_SERVERS_HEALTHY",
      "summary" : "GOOD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "Oozie"
  }, {
    "name" : "impala",
    "type" : "IMPALA",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://ip-172-31-13-124.ap-southeast-2.compute.internal:7180/cmf/serviceRedirect/impala",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "IMPALA_ASSIGNMENT_LOCALITY",
      "summary" : "DISABLED"
    }, {
      "name" : "IMPALA_CATALOGSERVER_HEALTH",
      "summary" : "GOOD"
    }, {
      "name" : "IMPALA_IMPALADS_HEALTHY",
      "summary" : "GOOD"
    }, {
      "name" : "IMPALA_STATESTORE_HEALTH",
      "summary" : "GOOD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "Impala"
  }, {
    "name" : "yarn",
    "type" : "YARN",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://ip-172-31-13-124.ap-southeast-2.compute.internal:7180/cmf/serviceRedirect/yarn",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "YARN_JOBHISTORY_HEALTH",
      "summary" : "GOOD"
    }, {
      "name" : "YARN_NODE_MANAGERS_HEALTHY",
      "summary" : "GOOD"
    }, {
      "name" : "YARN_RESOURCEMANAGERS_HEALTH",
      "summary" : "GOOD"
    }, {
      "name" : "YARN_USAGE_AGGREGATION_HEALTH",
      "summary" : "DISABLED"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "YARN (MR2 Included)"
  }, {
    "name" : "hdfs",
    "type" : "HDFS",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://ip-172-31-13-124.ap-southeast-2.compute.internal:7180/cmf/serviceRedirect/hdfs",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "HDFS_BLOCKS_WITH_CORRUPT_REPLICAS",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_CANARY_HEALTH",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_DATA_NODES_HEALTHY",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_FREE_SPACE_REMAINING",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_HA_NAMENODE_HEALTH",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_MISSING_BLOCKS",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_UNDER_REPLICATED_BLOCKS",
      "summary" : "GOOD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "HDFS"
  } ]
}