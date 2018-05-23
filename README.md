# kubernetes-kops-handson

## Requirements

- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- [kops](https://github.com/kubernetes/kops)
- [aws-cli](https://github.com/aws/aws-cli)


## Basic Settings (kops)

### ~/.aws/credentials

```
[your-profile-name]
aws_access_key_id = your-aws-access-key
aws_secret_access_key = your-aws-secret-access-key
region = your-region (e.g. ap-northeast-1)
```

### Enviroment Variables

```
export NAME=your-k8s-context-name (e.g. k8s.example.com)
export KOPS_STATE_STORE=your-state-store-path (e.g. s3://clusters.k8s.example.com)
export AWS_DEFAULT_PROFILE=your-aws-profile-name (e.g. k8s-user)
export AWS_ACCESS_KEY_ID=your-aws-access-key
export AWS_SECRET_ACCESS_KEY=your-aws-secret-access-key
```

## Usage

* [Create Cluster](/docs/kops/cluster_create.md)
* [Update Cluster](/docs/kops/cluster_update.md)
