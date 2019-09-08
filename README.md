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

# 2. Horizontal Pod Autoscaling

## Preparation
First of all, to use Horizontal Pod Autoscaling, you need to deploy [wide-camp-1909/metrics-server](https://github.com/wide-camp-1909/metrics-server) in namespace kube-system.  
Run the following and you can done the preparation:

```
% git clone -b camp-master --depth 1 https://github.com/wide-camp-1909/metrics-server
% cd metrics-server
% kubectl apply -f deploy/1.8+/
% kubectl describe deployment metrics-server -n kube-system
% kubectl top nodes
```

# 3. Build Docker Private Registry
Run the following:
```bash
$ kubectl create secret -n camp-dns \
          docker-registry camp-reg \
          --docker-server="REG-IP-ADDRESS:PORT" \
          --docker-username="USER-NAME" \
          --docker-password="PASSWORD" \
          -o yaml --dry-run | kubectl replace -n camp-dns --force -f -
```

After the above deployment, you can login private registry and push images:
```bash
$ docker login https://REG-IP-ADDRESS:PORT/v2/
$ docker push
```
