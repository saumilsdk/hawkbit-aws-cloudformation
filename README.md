# hawkbit-aws-cloudformation
Serverless project which deploy Hawkbit Update Server on aws using cloudformation with ELB

# Install serverless
```
npm install serverless -g
```

# Setup aws credentials
```
serverless config credentials --provider aws --key abc --secret xyz
```
# Deploy the hawkbit update-server 
```
serverless deploy
```

This will setup following infrastructure in the AWS us-east-1 region
1. Elastic Container Service(ECS) Cluster named "Hawkbit-cluster"
2. ECS Fargate service named "hawkbit-service"
3. ECS Fargate Task "HawkbitStartServerTask" under the service
4. Task container "hawkbit-container" under the task
5. CloudWatch log configuration for the container to log hawkbit logs
6. Elastic Load Balancer of type application to point to "hawkbit-service"
7. Network infrastructure like subnets, gateway, route tables etc for ELB
8. IAM Role and policies for "HawkbitStartServerTask" to execute
9. Use the stack output variable "HawkbitLoadBalancerEndPoint" to connect to hawkbit UI
