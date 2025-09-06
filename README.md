# CKA-exam-prep
This repository is a collection of the information I gathered while preparing for Certified Kubernetes Administrator exam. 


### Common commands

Create from a definition file:
```
kubectl create -f <filename>
```

Replace object using a definition file:
```
kubectl replace -f <filename>
```

View information about the resources:
```
kubectl get <resource-kind> <resource-name>
```

View detailed information about the resource:
```
kubectl describe <resource-kind> <resource-name>
```

Remove resources:
```
kubectl delete <resource-kind> <resource-name>
```

Change number of replicas:
```
kubectl scale --replicas=<number> -f <filename>
```
