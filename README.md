# devops-on-aws

Deploy [Demo Application](https://github.com/davidlu1001/aws_devops_todo/tree/final) to ECS and EKS

## Deploy app to ECS Cluster

```
> export AWS_PROFILE=<profile>   

> aws cloudformation deploy --template-file stack.yml \
	--stack-name todobackend --parameter-overrides $(cat dev.json) \
	--capabilities CAPABILITY_NAMED_IAM
```
### Or to simplify, to deploy to the `Dev` environment
```
# Update dev.json file
> vim dev.json

# Deploy to Dev
> make deploy/dev
```

### To deploy to the `Prod` environment (if `prod.json` exists)
```
# Update prod.json file
> vim prod.json

# Deploy to Prod
> make deploy/prod
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