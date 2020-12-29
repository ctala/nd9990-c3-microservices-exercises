aws eks --region us-west-2 update-kubeconfig --name Udacity3 --profile ctala  


## APPLY COnfiguration
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml

kubectl apply -f load-balancer.yaml

kubectl create -f configmap.yaml

## Interacting
kubectl get all

kubectl get pods
kubectl get pod PODNAME
kubectl logs PODNAME


kubectl exec -it pod/my-app-744cf947bf-tfrxb -- /bin/bash
kubectl exec -it pod/reverse-proxy-6bdcfb6f67-g488q -- sh

kubectl exec -it  pod/my-app-front-5484bdbfdd-9rsv7
kubectl describe services - show the services in the cluster
kubectl cluster-info - display information about the cluster



curl -o aws-iam-authenticator https://amazon-eks.s3.us-west-2.amazonaws.com/1.18.9/2020-11-02/bin/linux/amd64/aws-iam-authenticator


aws eks --region us-west-2 update-kubeconfig --name Udacity2 --profile ctala


kubectl scale deployment.apps/my-app --replicas=2


kubectl autoscale deployment reverse-proxy --cpu-percent=50 --min=2 --max=10


# Creating Zip File for project Submission

```bash
zip -r project.zip project -x *.git* */node_modules/**\*
```


## Create metrics server

https://docs.aws.amazon.com/eks/latest/userguide/metrics-server.html

The Kubernetes Metrics Server is an aggregator of resource usage data in your cluster, and it is not deployed by default in Amazon EKS clusters. The Metrics Server is commonly used by other Kubernetes add ons, such as the Horizontal Pod Autoscaler or the Kubernetes Dashboard. For more information, see Resource metrics pipeline

in the Kubernetes documentation. This topic explains how to deploy the Kubernetes Metrics Server on your Amazon EKS cluster.

To deploy the Metrics Server

    Deploy the Metrics Server with the following command:

```kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/download/v0.3.7/components.yaml```

Verify that the metrics-server deployment is running the desired number of pods with the following command.

```kubectl get deployment metrics-server -n kube-system```

Output

NAME             READY   UP-TO-DATE   AVAILABLE   AGE
metrics-server   1/1     1            1           6m