Following shows some hadoop commands:

|Command|Usage|
|---|---|
|hadoop fs -ls|list of files and directories in HDFS|
|hadoop fs -put FileName|upload a file into HDFS|
|hadoop fs -mv oldFile newFile|rename a file|
|hadoop fs -rm FileName|remove a file|
|hadoop fs -mkdir Dir|make a directory in HDFS|


Hadoop consists of a number of mappers which reads data and generate a mapping between a key and a value (i.e. \<key, value\>). Then shuffle and sort will take place. After that reducer just combine the results of mappers.

##Run your MapReduce:

After writing mapper and reducer codes and testing them on local machine with a small data set, we can run it on hadoop using the following command:

*hs {mapper script} {reducer script} {input_file} {output directory}