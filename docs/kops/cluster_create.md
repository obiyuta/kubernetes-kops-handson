# Create Cluster

* Route 53: Create Hosted Zone
* Route 53: Configure DNS Setting
* S3: Create S3 Bucket
* kops: Create Cluster


## Route 53: Create Hosted Zone

```
aws route53 create-hosted-zone --profile profile-name --name $NAME --caller-reference 1
```

## Route 53: Configure DNS Setting

Register the NS record of created hosted zone to application's hosted zone as well.

### Hosted Zone / k8s.example.com

|Name|Type|Value|
|--|--|--|
|k8s.example.jp.|NS|ns-xxx.awsdns-xx.co.uk. <br>ns-xxx.awsdns-xx.net.<br>ns-xxxx.awsdns-xx.org.<br>ns-xxx.awsdns-xx.com.|

### Hosted Zone / example.com

|Name|Type|Value|
|--|--|--|
|k8s.example.jp.|NS|ns-xxx.awsdns-xx.co.uk. <br>ns-xxx.awsdns-xx.net.<br>ns-xxxx.awsdns-xx.org.<br>ns-xxx.awsdns-xx.com.|

※ Both `k8s.example.com` and `example.com` have the same NS record.

__Check your NS record__

```
$ dig +short k8s.example.jp ns
```

## S3: Create S3 bucket

Create a S3 bucket for managing your cluster configuration.

```
$ aws s3 mb $KOPS_STATE_STORE --region ap-northeast-1 --profile your-profile-name
```

Enable the bucket "Versioning" to rollback the cluster configuration.

```
$ aws s3api put-bucket-versioning --bucket clusters.k8s.example.com --profile your-profile-name --versioning-configuration Status=Enabled 
```

※ Use this bucket as `KOPS_STATE_STORE`


## kops: Create Cluster Configuration

```
kops create cluster \
--name $NAME \
--zones ap-northeast-1a,ap-northeast-1c \
--state $KOPS_STATE_STORE \
--yes
```

## Kops: Create Cluster

```
kops update cluster $NAME --yes
```

__Check Cluster Status__

```
$ kubectl get nodes // or `kubectl get no`
```

```
NAME                                               STATUS    ROLES     AGE       VERSION
ip-xxx-xx-xx-xxx.ap-northeast-1.compute.internal   Ready     node      10s        v1.8.4
ip-xxx-xx-xx-xxx.ap-northeast-1.compute.internal   Ready     master    10s       v1.8.4
ip-xxx-xx-xx-xxx.ap-northeast-1.compute.internal   Ready     node      10s        v1.8.4
```

## Kips: Import Context

```
kops export kubecfg $NAME
```