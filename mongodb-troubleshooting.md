
# MongoDB Database Troubleshooting

## Beginner:
### Check Database Status
```bash
mongod --version  # Check MongoDB version
use <dbname>  # Switch to specific database
show dbs  # List available databases
show collections  # List collections in the current database
```

### Check Server Health
```bash
db.serverStatus()  # Get server status
db.stats()  # Get database statistics
```

### Check Database Connections
```bash
db.currentOp()  # View current operations
db.serverStatus().connections  # View active connections
```

## Intermediate:
### Check Slow Queries
```bash
db.setProfilingLevel(1)  # Enable slow query profiling
db.system.profile.find().sort({ts:-1}).limit(5)  # View last 5 slow queries
```

### Check Index Usage
```bash
db.collection.getIndexes()  # View indexes in a collection
db.collection.aggregate([{$indexStats}])  # View index stats
```

### Check Database Locks
```bash
db.currentOp({$and:[{waitingForLock:true},{opid:{$ne:1}}]})  # Find operations waiting for locks
```

## Advanced:
### Sharding and Replication Troubleshooting
```bash
sh.status()  # View sharded cluster status
rs.status()  # Check replica set status
```

### Performance Tuning
```bash
db.collection.explain("executionStats").find(<query>)  # Query performance analysis
```

### Memory Usage
```bash
db.serverStatus().mem  # View memory usage
```
