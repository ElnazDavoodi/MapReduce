Following shows Hadoop map reduce ecosystem:

![hadoop_ecosystem](https://cloud.githubusercontent.com/assets/13399252/18800655/247bd056-81ac-11e6-947f-01c6e35db0db.png)

The core Hadoop project consists of a way to store data, known as the Hadoop Distributed File System, or HDFS, and a way to process the data, called MapReduce.

##Hadoop Distributed File System (HDFS)

Files are stored in HDFS. When a file is uploaded into HDFS, it will be split into chunks, called *''block''*. The default size of each block is 64 MB. The last block of the file may be smaller than the default size. 


Hadoop performs the map reduce on the cluster (cloud cluster). There’s a daemon, or piece of software, running on each of these *cluster nodes* called the **DataNode**, which takes care of storing the blocks. Each block is processed on one cluster node and all cluster nodes are working in parallel. We need to know which block is running on each cluster node. This is handled by a daemon called the **NameNode**.

![Hadoop cluster](https://cloud.githubusercontent.com/assets/13399252/18801616/deb96e24-81b1-11e6-9ce2-7cee4d5aee3d.png)

##Data Redundancy:
The problem with this system is that if one node fails, a part of data will be missed. Hadoop resolves this problem by making 3 copies of each block and run each on separate node.

![Hadoop_data redundancy](https://cloud.githubusercontent.com/assets/13399252/18801884/8c76dac8-81b3-11e6-8c70-48193574ad4e.png)

##Problem with NameNode:

If NameNode is become inaccessible, there is no way to figure out which block belongs to which file (or what part of the file). One way to solve this problem, is to keep a copy of the NameNode somewhere in the network using NFS, which is a method of mounting a remote disk on the NameNode. Another way is to have two copies of NameNode: *active* and *standby*. Active NameNode works as before; while standby will be used if active NameNode fails.   





