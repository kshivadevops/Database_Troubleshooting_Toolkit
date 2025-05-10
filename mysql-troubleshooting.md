
# MySQL Database Troubleshooting

## Beginner:
### Check Database Status
```bash
mysqladmin -u root -p status  # Check the basic status of MySQL server
SHOW DATABASES;  # List available databases
SHOW TABLES;  # List tables in the current database
SHOW PROCESSLIST;  # Show active processes
```

### Check Server Health
```bash
SHOW VARIABLES LIKE 'uptime';  # Check server uptime
SHOW VARIABLES LIKE 'version';  # Check MySQL version
SHOW ENGINE INNODB STATUS;  # View InnoDB engine status for lock issues
```

### Check Database Connections
```bash
netstat -an | grep 3306  # Check if MySQL is listening on default port
mysql -h <hostname> -u <username> -p  # Test database connection
```

## Intermediate:
### Check Performance
```bash
SHOW STATUS LIKE 'Threads%';  # View thread usage
SHOW STATUS LIKE 'Questions';  # View number of queries processed
EXPLAIN <query>;  # Get query execution plan
```

### View Slow Queries
```bash
SHOW VARIABLES LIKE 'slow_query_log';  # Check if slow query logging is enabled
SHOW VARIABLES LIKE 'long_query_time';  # View slow query threshold
tail -f /var/log/mysql/mysql-slow.log  # Monitor slow query logs in real-time
```

### Check Locks
```bash
SHOW ENGINE INNODB STATUS\G  # View InnoDB engine locks and deadlocks
SELECT * FROM information_schema.innodb_lock_waits;  # View lock waits
```

## Advanced:
### Query Performance Tuning
```bash
SHOW STATUS LIKE 'Handler%';  # View handler stats (fetching rows)
SHOW TABLE STATUS LIKE '<table_name>';  # Table-level stats
OPTIMIZE TABLE <table_name>;  # Optimize a table
```

### Analyze Resource Utilization
```bash
SHOW GLOBAL STATUS LIKE 'Com%';  # View command statistics
SHOW GLOBAL STATUS LIKE 'Innodb_buffer_pool%';  # Buffer pool stats
```

### Database Replication Issues
```bash
SHOW SLAVE STATUS\G  # Check replication slave status
SHOW MASTER STATUS;  # View master server status
```
