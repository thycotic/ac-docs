[title]: # (Database Replication)
[tags]: # (remote access controller)
[priority]: # (5)
# Configure Database Replication

1. While logged into MySQL on Server 1, query the master status:

   `SHOW MASTER STATUS;`

   Note the file and position values that are displayed:

   ```sql
      mysql> SHOW MASTER STATUS;
      +------------------+----------+--------------+------------------+
      | File             | Position | Binlog_Do_DB | Binlog_Ignore_DB |
      +------------------+----------+--------------+------------------+
      | mysql-bin.000001 |      277 |              |                  |
      +------------------+----------+--------------+------------------+
      1 row in set (0.00 sec)
   ```
1. On Server 2 at the MySQL prompt, set up the slave functionality for that database. Replace x.x.x.x with the private IP from the first server. Also replace the value for master_log_file with the file value from the previous step, and the value for master_log_pos with the position value.

   ```sql
      STOP SLAVE;
      CHANGE MASTER TO master_host='x.x.x.x', master_port=3306, master_user='replication', master_password='password', master_log_file='mysql-bin.000001', master_log_pos=106;
      START SLAVE;
   ```

   For example:

   ```sql
      STOP SLAVE;
      CHANGE MASTER TO master_host='192.168.122.50', master_port=3306, master_user='replication', master_password='password', master_log_file='mysql-bin.000001', master_log_pos=277;
      START SLAVE;
   ```
1. On Server 2, query the master status. Again note the file and position values.

   ```sql
      SHOW MASTER STATUS;

      mysql> SHOW MASTER STATUS;
      +------------------+----------+--------------+------------------+
      | File             | Position | Binlog_Do_DB | Binlog_Ignore_DB |
      +------------------+----------+--------------+------------------+
      | mysql-bin.000002 |      377 |              |                  |
      +------------------+----------+--------------+------------------+
      1 row in set (0.00 sec)
   ```
1. Set the slave database status on Server 1, replacing the same values swapped in step 2 with those from the Server 2.

   ```sql
      STOP SLAVE;
      CHANGE MASTER TO master_host='x.x.x.x', master_port=3306, master_user='replication', master_password='password', master_log_file='mysql-bin.000001', master_log_pos=778;
      START SLAVE;
   ```
   For example:

   ```sql
      STOP SLAVE;
      CHANGE MASTER TO master_host='192.168.122.51', master_port=3306, master_user='replication', master_password='password', master_log_file='mysql-bin.000002', master_log_pos=377;
      START SLAVE;
   ```
