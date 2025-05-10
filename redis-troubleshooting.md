
# Redis Database Troubleshooting

## Beginner:
### Check Redis Status
```bash
redis-server --version  # Check Redis version
redis-cli INFO  # Get server information
```

### Check Server Health
```bash
redis-cli ping  # Check if Redis server is responsive
redis-cli INFO memory  # Check memory usage
redis-cli INFO stats  # Get Redis server stats
```

### Check Connections
```bash
redis-cli CLIENT LIST  # List active Redis clients
```

## Intermediate:
### Check Slow Queries
```bash
redis-cli SLOWLOG GET 10  # Get the last 10 slow queries
redis-cli CONFIG SET slowlog-log-slower-than <time>  # Set slow query threshold
```

### Memory Issues
```bash
redis-cli MEMORY STATS  # View Redis memory stats
redis-cli MEMORY USAGE <key>  # Check memory usage of a specific key
```

## Advanced:
### Persistence Troubleshooting
```bash
redis-cli CONFIG GET dir  # Check directory for Redis data
redis-cli SAVE  # Trigger a save to disk manually
```

### Replication Issues
```bash
redis-cli INFO replication  # Check replication status
```

### Cluster Troubleshooting
```bash
redis-cli CLUSTER INFO  # View cluster status
redis-cli CLUSTER NODES  # List Redis cluster nodes
```
