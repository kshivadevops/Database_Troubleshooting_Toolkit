
# PostgreSQL Database Troubleshooting

## Beginner:
### Check Database Status
```bash
psql -U postgres -h localhost -c "SELECT version();"  # Check PostgreSQL version
psql -U postgres -l  # List available databases
ps aux | grep postgres  # List PostgreSQL processes
```

### Check Server Health
```bash
pg_isready  # Check if PostgreSQL is ready
SHOW server_version;  # Get PostgreSQL version
```

### Check Database Connections
```bash
psql -U <user> -d <dbname>  # Test connection to a specific database
SELECT * FROM pg_stat_activity;  # View active database connections
```

## Intermediate:
### Check Database Performance
```bash
EXPLAIN ANALYZE <query>;  # Get query execution plan
SELECT pg_stat_activity, pg_locks FROM pg_catalog.pg_stat_activity;  # Check for locking issues
SELECT * FROM pg_stat_user_tables;  # Table performance stats
```

### View Long-Running Queries
```bash
SELECT * FROM pg_stat_activity WHERE state = 'active' AND now() - query_start > interval '1 minute';  # Find long-running queries
```

### Check Autovacuum
```bash
SHOW autovacuum;  # Check if autovacuum is enabled
SELECT * FROM pg_stat_user_tables WHERE n_dead_tup > 0;  # Find tables needing vacuum
```

## Advanced:
### Index and Table Performance Tuning
```bash
SELECT * FROM pg_stat_user_indexes WHERE idx_scan = 0;  # Find unused indexes
REINDEX TABLE <table_name>;  # Rebuild indexes
```

### Database Lock Troubleshooting
```bash
SELECT * FROM pg_locks WHERE NOT granted;  # Find blocked transactions
SELECT pid, pg_terminate_backend(pid) FROM pg_stat_activity WHERE state = 'idle in transaction';  # Terminate idle connections
```

### Replication Troubleshooting
```bash
SELECT * FROM pg_stat_replication;  # View replication status
SELECT * FROM pg_stat_wal_receiver;  # View WAL receiver status
```
