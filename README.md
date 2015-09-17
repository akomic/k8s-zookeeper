ZooKeeper on Docker for Kubernetes
================================

Creating docker container for single or multi-node Zookeeper cluster that can run on Kubernetes.

# Single node

To start Zookeeper as single node

```
docker run akomic/zookeeper
```

# Multi node

## To start Zookeeper multi-node cluster (3 nodes)

```
docker run -e SERVER_ID=1 -e MAX_SERVERS=3 --name zookeeper-1 --restart=always akomic/zookeeper
docker run -e SERVER_ID=2 -e MAX_SERVERS=3 --name zookeeper-2 --restart=always akomic/zookeeper
docker run -e SERVER_ID=3 -e MAX_SERVERS=3 --name zookeeper-3 --restart=always akomic/zookeeper
```

NOTICE: For this to work you need to provide the means for container to
resolve node hosts (zookeeper-1, zookeeper-2, zookeeper-3) which is beyond
the scope of this document. You can do this with your own DNS, or just use
Kubernetes and json below.

## To start Zookeeper multi-node on Kubernetes (3 nodes)

```
kubectl create -f zookeeper_config.json
```
