ZooKeeper 2
===============
This Zookeeper requires that the config file be on the local machine that it is running on.

Requires files to be mapped in:
* zoo.cfg
* myid

## Starting the Container

     docker run -d \
     -v /opt/zookeeper/conf/zoo.cfg:/opt/zookeeper/conf/zoo.cfg \
     -v /opt/zookeeper:/tmp/zookeeper \
     -p 2181:2181 \
     -p 2888:2888 \
     -p 3888:3888 \
     vungle/zookeeper2:dev
     
The `/opt/zookeeper` directory should contain the `myid` file.  This is also where Zookeeper will put
its data once it starts up.
     
## Sample myid config

    1234
         
## Sample zoo.cfg config

     # The number of milliseconds of each tick
     tickTime=2000
     # The number of ticks that the initial 
     # synchronization phase can take
     initLimit=10
     # The number of ticks that can pass between 
     # sending a request and getting an acknowledgement
     syncLimit=5
     # the directory where the snapshot is stored.
     # do not use /tmp for storage, /tmp here is just 
     # example sakes.
     dataDir=/tmp/zookeeper
     # the port at which the clients will connect
     clientPort=2181
     # the maximum number of client connections.
     # increase this if you need to handle more clients
     #maxClientCnxns=60
     #
     # Be sure to read the maintenance section of the 
     # administrator guide before turning on autopurge.
     #
     # http://zookeeper.apache.org/doc/current/zookeeperAdmin.html#sc_maintenance
     #
     # The number of snapshots to retain in dataDir
     #autopurge.snapRetainCount=3
     # Purge task interval in hours
     # Set to "0" to disable auto purge feature
     #autopurge.purgeInterval=1
     server.71422762=172.16.31.246:2888:3888
     server.3912285=172.16.31.247:2888:3888
     server.3912306=172.16.32.186:2888:3888
     server.3912291=172.16.32.92:2888:3888
     server.71421963=172.16.33.211:2888:3888
     
## CoreOS machine setup

There are Ansible playbooks to help provision up a CoreOS machine with the folders and files it needs:

https://github.com/Vungle/ansible