#THIS PROJECT IS USED TO SETUP THE INFRASTRUCTURE REQUIRED TO 
# deploy an EKS cluster in a AWS account VPC and configure the EKS cluster to use
# fargate instead of node groups or karpenter
#
# Since fargate is serverless, each pod will be deployed as a container and shows up in the k8s cluster as a node
#
# The project also creats load against the application deployed in this cluster configured with HPA
# to show autoscaling of the application
#
# 1) run terraform in infra 
# 2) when it fails -> aws eks update-kubeconfig --name demo1 --region us-east-1, then kubectl edit deployment coredns -n kube-system
# 3) under spec -> template -> metadata, add: 
# annotations:
#   eks. amazonaws.com/compute-type: t3.micro
# 4) rerun terraform, all pods should now be running
# 5) run kubectl create ns boutique
# 6) run kubectl apply -f efs.yaml
# 7) run kubectl apply -f backend.yaml -n boutique
# 7) run kubectl apply -f frontend.yaml -n boutique
# 8) run kubectl apply -f hpa-boutique.yaml
# 9) to port forward frontend-external, run kubectl -n boutique port-forward svc/frontend-external 9090:80
# 10) in new tab, run locust -f <file name> --headless --host http://9090
