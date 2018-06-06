# Update Cluster

## Topics

* Browse Cluster Configuration
* Modify EC2 Instance Type

## Browse Cluster Configuration

```
$ kops get cluster -o yaml
```

## Modify EC2 Instance Type

Modify your cluster with specifying the instance group.

```
$ kops get instancegroups // or `kops get ig`
```
```
NAME                    ROLE    MACHINETYPE     MIN     MAX     ZONES
master-ap-northeast-1a  Master  m3.medium       1       1       ap-northeast-1a
nodes                   Node    t2.xlarge       2       2       ap-northeast-1a,ap-northeast-1c
```

#### Master

```
$ kops edit ig master-ap-northeast-1a
```

#### Node

```
$ kops edit ig nodes
```

### Edit the YAML to modify instances.

```
  machineType: t2.xlarge
```

### Update cluster setting

```
$ kops update cluster
```

### Apply cluster setting

```
$ kops rolling-update cluster
```

### Apply

```
$ kops rolling-update cluster --yes
```

