# 1. Use NFS as Persistent Volume

## Preparation of NFS Mouting
Run below installation at each hosts:
```
% apt install nfs-common
% yay -S nfs-utils
```

## I/O Performance of NFS
### Read
```
% kc logs -f nfs-read-performance-test-xjrwj
262143+1 records in
262143+1 records out
2147479552 bytes (2.1 GB, 2.0 GiB) copied, 22.0823 s, 97.2 MB/s
```

### Write
```
% kc logs -f nfs-write-performance-test-f6bls
0+1 records in
0+1 records out
2147479552 bytes (2.1 GB, 2.0 GiB) copied, 43.8197 s, 49.0 MB/s
```

## Elasticsearch with NFS Backend
Running ES with NFS is **not supported and known to be problematic,** also performance will be very low.  
See: https://discuss.elastic.co/t/elasticsearch-not-able-to-use-persistent-volume/133390

