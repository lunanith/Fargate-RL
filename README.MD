#THIS PROJECT IS USED TO SETUP THE INFRASTRUCTURE REQUIRED TO 
# deploy an EKS cluster in a AWS account VPC and configure the EKS cluster to use
# fargate instead of node groups or karpenter
#
# Since fargate is serverless, each pod will be deployed as a container and shows up in the k8s cluster as a node
#
# The project also creats load against the application deployed in this cluster configured with HPA
# to show autoscaling of the application
#
