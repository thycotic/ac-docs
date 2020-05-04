[title]: # (Database Setup)
[tags]: # (remote access controller)
[priority]: # (4)
# Mysql Master/Master Setup

Assume we have 2 servers with private IP = `192.168.122.50` & `192.168.122.51`

**Private network:** 192.168.122.0/24

>**Note**: Please use private IPs for replication to provide more security.

## Add Firewall Rule

To allow mysql port can be connected through this private network. Execute following command on both servers:

```bash
   ufw allow from 192.168.122.0/24 to any port 3306
```

## Update Server 2

Apply latest mysqldump data from Server 1, if they have different DB data.

### Edit MySQL’s Configuration

Edit the /etc/mysql/mysql.conf.d/mysqld.cnf file on each of the servers. Add the following values:

#### Server 1

```sql
[mysqld]
server_id           = 1
log_bin             = /var/log/mysql/mysql-bin.log
log_bin_index       = /var/log/mysql/mysql-bin.log.index
relay_log           = /var/log/mysql/mysql-relay-bin
relay_log_index     = /var/log/mysql/mysql-relay-bin.index
expire_logs_days    = 10
max_binlog_size     = 100M
log_slave_updates   = 1
auto-increment-increment = 2
auto-increment-offset = 1
```

#### Server 2

```sql
[mysqld]
server_id           = 2
log_bin             = /var/log/mysql/mysql-bin.log
log_bin_index       = /var/log/mysql/mysql-bin.log.index
relay_log           = /var/log/mysql/mysql-relay-bin
relay_log_index     = /var/log/mysql/mysql-relay-bin.index
expire_logs_days    = 10
max_binlog_size     = 100M
log_slave_updates   = 1
auto-increment-increment = 2
auto-increment-offset = 2
```

**auto_increment_increment** = controls the increment between successive AUTO_INCREMENT values.  
**auto_increment_offset** = determines the starting point for AUTO_INCREMENT column values.

>**Note**: Let's assume we have N MySQL nodes (N=4 in this example), then auto_increment_increment has the value N on all nodes, and each node must have a different value for auto_increment_offset (1, 2, ..., N).
>We also need to configure log-slave-updates because otherwise replication will work only, for example, from server1 to server2, but not to server3 and server4.

Once completed, restart the MySQL application:

```sql
systemctl restart mysql

```

## Create Replication Users

1. Log in to MySQL as root on each of the servers: Configure the replication users on each server.  
Replace x.x.x.x with the private IP address of the other server, and password with a strong password:

```sql
mysql -u root -p

GRANT REPLICATION SLAVE ON *.* TO 'replication'@'x.x.x.x' IDENTIFIED BY 'password';
```

### For Example

#### Server 1


```sql
GRANT REPLICATION SLAVE ON *.* TO 'replication'@'192.168.122.51' IDENTIFIED BY 'password';

```

#### Server 2

```sql
GRANT REPLICATION SLAVE ON *.* TO 'replication'@'192.168.122.50' IDENTIFIED BY 'password';

```
