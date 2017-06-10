./sqlline.py <your_zookeeper_quorum>

# Connecting to the command line - 
```
/usr/hdp/2.6.1.0-129/phoenix/bin/sqlline.py server0.mydomain.com,server1.mydomain.com,server2.mydomain.com:2181:/hbase-unsecure
```

# Loading CSV data from CLI (Data file name MUST have extension .csv)
```
/usr/hdp/2.6.1.0-129/phoenix/bin/psql.py -t EXAMPLE localhost data.csv
```
