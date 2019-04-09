SQOOP EXERCISE
EXERCISE1-1

0)필드찾기(실행문)
[training@localhost ~]$ sqoop eval \
> --connect jdbc:mysql://localhost/loudacre \
> --username training --password training \
> --query "describe accounts"
(결과)
19/04/08 18:26:03 INFO sqoop.Sqoop: Running Sqoop version: 1.4.6-cdh5.7.0
19/04/08 18:26:03 WARN tool.BaseSqoopTool: Setting your password on the command-line is insecure. Consider using -P instead.
19/04/08 18:26:03 INFO manager.MySQLManager: Preparing to use a MySQL streaming resultset.
---------------------------------------------------------------------------------------------------------
| Field                | Type                 | Null | Key | Default              | Extra                |
---------------------------------------------------------------------------------------------------------
| acct_num             | int(11)              | NO  | PRI | (null)               |                      |
| acct_create_dt       | datetime             | NO  |     | (null)               |                      |
| acct_close_dt        | datetime             | YES |     | (null)               |                      |
| first_name           | varchar(255)         | NO  |     | (null)               |                      |
| last_name            | varchar(255)         | NO  |     | (null)               |                      |
| address              | varchar(255)         | NO  |     | (null)               |                      |
| city                 | varchar(255)         | NO  |     | (null)               |                      |
| state                | varchar(255)         | NO  |     | (null)               |                      |
| zipcode              | varchar(255)         | NO  |     | (null)               |                      |
| phone_number         | varchar(255)         | NO  |     | (null)               |                      |
| created              | datetime             | NO  |     | (null)               |                      |
| modified             | datetime             | NO  |     | (null)               |                      |
---------------------------------------------------------------------------------------------------------


1)실행문
 --connect jdbc:mysql://localhost/loudacre \
> --username training --password training \
> --table accounts \
> --columns "acct_num, first_name, last_name" \
> --target-dir /loudacre/accounts \
> --fields-terminated-by "\t"

2) 결과

19/04/07 22:58:54 INFO sqoop.Sqoop: Running Sqoop version: 1.4.6-cdh5.7.0
19/04/07 22:58:54 WARN tool.BaseSqoopTool: Setting your password on the command-line is insecure. Consider using -P instead.

19/04/07 22:58:54 INFO manager.MySQLManager: Preparing to use a MySQL streaming resultset.
19/04/07 22:58:54 INFO tool.CodeGenTool: Beginning code generation
19/04/07 22:58:54 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/07 22:58:55 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/07 22:58:55 INFO orm.CompilationManager: HADOOP_MAPRED_HOME is /usr/lib/hadoop-mapreduce
Note: /tmp/sqoop-training/compile/94ce2b3fb488eafded2902895773dcbf/accounts.java uses or overrides a deprecated API.
Note: Recompile with -Xlint:deprecation for details.
19/04/07 22:58:56 INFO orm.CompilationManager: Writing jar file: /tmp/sqoop-training/compile/94ce2b3fb488eafded2902895773dcbf/accounts.jar
19/04/07 22:58:57 WARN manager.MySQLManager: It looks like you are importing from mysql.
19/04/07 22:58:57 WARN manager.MySQLManager: This transfer can be faster! Use the --direct
19/04/07 22:58:57 WARN manager.MySQLManager: option to exercise a MySQL-specific fast path.
19/04/07 22:58:57 INFO manager.MySQLManager: Setting zero DATETIME behavior to convertToNull (mysql)
19/04/07 22:58:57 INFO mapreduce.ImportJobBase: Beginning import of accounts
19/04/07 22:58:57 INFO Configuration.deprecation: mapred.job.tracker is deprecated. Instead, use mapreduce.jobtracker.address
19/04/07 22:58:57 INFO Configuration.deprecation: mapred.jar is deprecated. Instead, use mapreduce.job.jar
19/04/07 22:58:58 INFO Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
19/04/07 22:58:58 INFO client.RMProxy: Connecting to ResourceManager at /0.0.0.0:8032
19/04/07 22:59:00 INFO db.DBInputFormat: Using read commited transaction isolation
19/04/07 22:59:00 INFO db.DataDrivenDBInputFormat: BoundingValsQuery: SELECT MIN(`acct_num`), MAX(`acct_num`) FROM `accounts`
19/04/07 22:59:00 INFO db.IntegerSplitter: Split size: 32440; Num splits: 4 from: 1 to: 129761
19/04/07 22:59:00 INFO mapreduce.JobSubmitter: number of splits:4
19/04/07 22:59:00 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1554697697270_0003
19/04/07 22:59:01 INFO impl.YarnClientImpl: Submitted application application_1554697697270_0003
19/04/07 22:59:01 INFO mapreduce.Job: The url to track the job: http://localhost:8088/proxy/application_1554697697270_0003/
19/04/07 22:59:01 INFO mapreduce.Job: Running job: job_1554697697270_0003
19/04/07 22:59:08 INFO mapreduce.Job: Job job_1554697697270_0003 running in uber mode : false
19/04/07 22:59:08 INFO mapreduce.Job:  map 0% reduce 0%
19/04/07 22:59:14 INFO mapreduce.Job:  map 25% reduce 0%
19/04/07 22:59:18 INFO mapreduce.Job:  map 50% reduce 0%
19/04/07 22:59:22 INFO mapreduce.Job:  map 75% reduce 0%
19/04/07 22:59:26 INFO mapreduce.Job:  map 100% reduce 0%
19/04/07 22:59:26 INFO mapreduce.Job: Job job_1554697697270_0003 completed successfully
19/04/07 22:59:26 INFO mapreduce.Job: Counters: 30
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=560384
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=470
		HDFS: Number of bytes written=2615920
		HDFS: Number of read operations=16
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=8
	Job Counters
		Launched map tasks=4
		Other local map tasks=4
		Total time spent by all maps in occupied slots (ms)=0
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=12887
		Total vcore-seconds taken by all map tasks=12887
		Total megabyte-seconds taken by all map tasks=3299072
	Map-Reduce Framework
		Map input records=129761
		Map output records=129761
		Input split bytes=470
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=181
		CPU time spent (ms)=3000
		Physical memory (bytes) snapshot=493731840
		Virtual memory (bytes) snapshot=8262221824
		Total committed heap usage (bytes)=251920384
	File Input Format Counters
		Bytes Read=0
	File Output Format Counters
		Bytes Written=2615920
19/04/07 22:59:26 INFO mapreduce.ImportJobBase: Transferred 2.4947 MB in 28.7679 seconds (88.8008 KB/sec)
19/04/07 22:59:26 INFO mapreduce.ImportJobBase: Retrieved 129761 records.
[training@localhost ~]$
[training@localhost ~]$ hdfs dfs -ls /loudacre/accounts
Found 5 items
-rw-rw-rw-   1 training supergroup          0 2019-04-07 22:59 /loudacre/accounts/_SUCCESS
-rw-rw-rw-   1 training supergroup     638090 2019-04-07 22:59 /loudacre/accounts/part-m-00000
-rw-rw-rw-   1 training supergroup     649567 2019-04-07 22:59 /loudacre/accounts/part-m-00001
-rw-rw-rw-   1 training supergroup     649000 2019-04-07 22:59 /loudacre/accounts/part-m-00002
-rw-rw-rw-   1 training supergroup     679263 2019-04-07 22:59 /loudacre/accounts/part-m-00003

EXERCISE1-2
 1) 실행문
 sqoop import \
--connect jdbc:mysql://localhost/loudacre \
--username training --password training \
--table accounts \
--compression-codec org.apache.hadoop.io.compress.SnappyCodec \
--target-dir /loudacre/accounts/user_compressed


 2) 결과
 19/04/07 23:11:49 INFO sqoop.Sqoop: Running Sqoop version: 1.4.6-cdh5.7.0
19/04/07 23:11:49 WARN tool.BaseSqoopTool: Setting your password on the command-line is insecure. Consider using -P instead.
19/04/07 23:11:49 INFO manager.MySQLManager: Preparing to use a MySQL streaming resultset.
19/04/07 23:11:49 INFO tool.CodeGenTool: Beginning code generation
19/04/07 23:11:50 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/07 23:11:50 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/07 23:11:50 INFO orm.CompilationManager: HADOOP_MAPRED_HOME is /usr/lib/hadoop-mapreduce
Note: /tmp/sqoop-training/compile/c2eb90e39db54ec01217e4ca242845d6/accounts.java uses or overrides a deprecated API.
Note: Recompile with -Xlint:deprecation for details.
19/04/07 23:11:52 INFO orm.CompilationManager: Writing jar file: /tmp/sqoop-training/compile/c2eb90e39db54ec01217e4ca242845d6/accounts.jar
19/04/07 23:11:52 WARN manager.MySQLManager: It looks like you are importing from mysql.
19/04/07 23:11:52 WARN manager.MySQLManager: This transfer can be faster! Use the --direct
19/04/07 23:11:52 WARN manager.MySQLManager: option to exercise a MySQL-specific fast path.
19/04/07 23:11:52 INFO manager.MySQLManager: Setting zero DATETIME behavior to convertToNull (mysql)
19/04/07 23:11:52 INFO mapreduce.ImportJobBase: Beginning import of accounts
19/04/07 23:11:52 INFO Configuration.deprecation: mapred.job.tracker is deprecated. Instead, use mapreduce.jobtracker.address
19/04/07 23:11:52 INFO Configuration.deprecation: mapred.jar is deprecated. Instead, use mapreduce.job.jar
19/04/07 23:11:52 INFO Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
19/04/07 23:11:53 INFO client.RMProxy: Connecting to ResourceManager at /0.0.0.0:8032
19/04/07 23:11:54 INFO db.DBInputFormat: Using read commited transaction isolation
19/04/07 23:11:54 INFO db.DataDrivenDBInputFormat: BoundingValsQuery: SELECT MIN(`acct_num`), MAX(`acct_num`) FROM `accounts`
19/04/07 23:11:54 INFO db.IntegerSplitter: Split size: 32440; Num splits: 4 from: 1 to: 129761
19/04/07 23:11:54 INFO mapreduce.JobSubmitter: number of splits:4
19/04/07 23:11:54 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1554697697270_0004
19/04/07 23:11:55 INFO impl.YarnClientImpl: Submitted application application_1554697697270_0004
19/04/07 23:11:55 INFO mapreduce.Job: The url to track the job: http://localhost:8088/proxy/application_1554697697270_0004/
19/04/07 23:11:55 INFO mapreduce.Job: Running job: job_1554697697270_0004
19/04/07 23:12:01 INFO mapreduce.Job: Job job_1554697697270_0004 running in uber mode : false
19/04/07 23:12:01 INFO mapreduce.Job:  map 0% reduce 0%
19/04/07 23:12:08 INFO mapreduce.Job:  map 25% reduce 0%
19/04/07 23:12:14 INFO mapreduce.Job:  map 50% reduce 0%
19/04/07 23:12:20 INFO mapreduce.Job:  map 75% reduce 0%
19/04/07 23:12:26 INFO mapreduce.Job:  map 100% reduce 0%
19/04/07 23:12:26 INFO mapreduce.Job: Job job_1554697697270_0004 completed successfully
19/04/07 23:12:27 INFO mapreduce.Job: Counters: 30
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=560960
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=470
		HDFS: Number of bytes written=8942356
		HDFS: Number of read operations=16
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=8
	Job Counters
		Launched map tasks=4
		Other local map tasks=4
		Total time spent by all maps in occupied slots (ms)=0
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=16815
		Total vcore-seconds taken by all map tasks=16815
		Total megabyte-seconds taken by all map tasks=4304640
	Map-Reduce Framework
		Map input records=129761
		Map output records=129761
		Input split bytes=470
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=280
		CPU time spent (ms)=5650
		Physical memory (bytes) snapshot=549896192
		Virtual memory (bytes) snapshot=8283389952
		Total committed heap usage (bytes)=251920384
	File Input Format Counters
		Bytes Read=0
	File Output Format Counters
		Bytes Written=8942356
19/04/07 23:12:27 INFO mapreduce.ImportJobBase: Transferred 8.5281 MB in 34.1011 seconds (256.0849 KB/sec)
19/04/07 23:12:27 INFO mapreduce.ImportJobBase: Retrieved 129761 records.

3) 캡쳐 of hue( 파일로 만들어짐)

exercise1-3
1) 실행문
sqoop import \
> --connect jdbc:mysql://localhost/loudacre \
> --username training --password training \
> --table accounts \
> --compression-codec org.apache.hadoop.io.compress.SnappyCodec \
> --target-dir /loudacre/accounts/user_compressed

2) 결과

19/04/07 23:22:29 INFO sqoop.Sqoop: Running Sqoop version: 1.4.6-cdh5.7.0
19/04/07 23:22:29 WARN tool.BaseSqoopTool: Setting your password on the command-line is insecure. Consider using -P instead.
19/04/07 23:22:30 INFO manager.MySQLManager: Preparing to use a MySQL streaming resultset.
19/04/07 23:22:30 INFO tool.CodeGenTool: Beginning code generation
19/04/07 23:22:30 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/07 23:22:30 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/07 23:22:30 INFO orm.CompilationManager: HADOOP_MAPRED_HOME is /usr/lib/hadoop-mapreduce
Note: /tmp/sqoop-training/compile/233d46bc44f3b4b4a876fbf95983e5cb/accounts.java uses or overrides a deprecated API.
Note: Recompile with -Xlint:deprecation for details.
19/04/07 23:22:32 INFO orm.CompilationManager: Writing jar file: /tmp/sqoop-training/compile/233d46bc44f3b4b4a876fbf95983e5cb/accounts.jar
19/04/07 23:22:32 WARN manager.MySQLManager: It looks like you are importing from mysql.
19/04/07 23:22:32 WARN manager.MySQLManager: This transfer can be faster! Use the --direct
19/04/07 23:22:32 WARN manager.MySQLManager: option to exercise a MySQL-specific fast path.
19/04/07 23:22:32 INFO manager.MySQLManager: Setting zero DATETIME behavior to convertToNull (mysql)
19/04/07 23:22:32 INFO mapreduce.ImportJobBase: Beginning import of accounts
19/04/07 23:22:32 INFO Configuration.deprecation: mapred.job.tracker is deprecated. Instead, use mapreduce.jobtracker.address
19/04/07 23:22:32 INFO Configuration.deprecation: mapred.jar is deprecated. Instead, use mapreduce.job.jar
19/04/07 23:22:33 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/07 23:22:33 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/07 23:22:33 INFO mapreduce.DataDrivenImportJob: Writing Avro schema file: /tmp/sqoop-training/compile/233d46bc44f3b4b4a876fbf95983e5cb/accounts.avsc
19/04/07 23:22:33 INFO Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
19/04/07 23:22:33 INFO client.RMProxy: Connecting to ResourceManager at /0.0.0.0:8032
19/04/07 23:22:35 INFO db.DBInputFormat: Using read commited transaction isolation
19/04/07 23:22:35 INFO db.DataDrivenDBInputFormat: BoundingValsQuery: SELECT MIN(`acct_num`), MAX(`acct_num`) FROM `accounts` WHERE ( state='CA' )
19/04/07 23:22:35 INFO db.IntegerSplitter: Split size: 32439; Num splits: 4 from: 1 to: 129760
19/04/07 23:22:35 INFO mapreduce.JobSubmitter: number of splits:4
19/04/07 23:22:35 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1554697697270_0005
19/04/07 23:22:36 INFO impl.YarnClientImpl: Submitted application application_1554697697270_0005
19/04/07 23:22:36 INFO mapreduce.Job: The url to track the job: http://localhost:8088/proxy/application_1554697697270_0005/
19/04/07 23:22:36 INFO mapreduce.Job: Running job: job_1554697697270_0005
19/04/07 23:22:43 INFO mapreduce.Job: Job job_1554697697270_0005 running in uber mode : false
19/04/07 23:22:43 INFO mapreduce.Job:  map 0% reduce 0%
19/04/07 23:22:50 INFO mapreduce.Job:  map 25% reduce 0%
19/04/07 23:22:57 INFO mapreduce.Job:  map 50% reduce 0%
19/04/07 23:23:04 INFO mapreduce.Job:  map 75% reduce 0%
19/04/07 23:23:10 INFO mapreduce.Job:  map 100% reduce 0%
19/04/07 23:23:11 INFO mapreduce.Job: Job job_1554697697270_0005 completed successfully
19/04/07 23:23:11 INFO mapreduce.Job: Counters: 30
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=566924
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=470
		HDFS: Number of bytes written=5669076
		HDFS: Number of read operations=16
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=8
	Job Counters
		Launched map tasks=4
		Other local map tasks=4
		Total time spent by all maps in occupied slots (ms)=0
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=20489
		Total vcore-seconds taken by all map tasks=20489
		Total megabyte-seconds taken by all map tasks=5245184
	Map-Reduce Framework
		Map input records=92416
		Map output records=92416
		Input split bytes=470
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=395
		CPU time spent (ms)=9780
		Physical memory (bytes) snapshot=608153600
		Virtual memory (bytes) snapshot=8283291648
		Total committed heap usage (bytes)=251920384
	File Input Format Counters
		Bytes Read=0
	File Output Format Counters
		Bytes Written=5669076
19/04/07 23:23:11 INFO mapreduce.ImportJobBase: Transferred 5.4065 MB in 38.2041 seconds (144.9113 KB/sec)
19/04/07 23:23:11 INFO mapreduce.ImportJobBase: Retrieved 92416 records.



3) 캡쳐 - 첨부 추가(1-3)
4) tojson 실행문(정상실행완료)
training@localhost ~]$ avro-tools tojson hdfs://localhost/loudacre/accounts/CA/part-m-00000.avro
