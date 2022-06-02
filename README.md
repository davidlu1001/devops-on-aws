# devops-on-aws

Deploy [Demo Application](https://github.com/davidlu1001/aws_devops_todo/tree/final) to ECS and EKS

## Deploy app to ECS Cluster

```
> export AWS_PROFILE=<profile>   

> aws cloudformation deploy --template-file stack.yml \
	--stack-name todobackend --parameter-overrides $(cat dev.json) \
	--capabilities CAPABILITY_NAMED_IAM
```

## Check ECS Cluster
```
# Check ECS Cluster
> aws ecs list-clusters
> aws ecs describe-clusters --cluster todobackend-cluster

# Check ALB Public URL
> aws cloudformation describe-stacks --stack-name todobackend --query
Stacks[].Outputs[]
```