*ReplicaSet* - is a modern alternative to the replication controller, using an updated API version and some improvements.

Key differences:
1. *apiVersion* - use `apps/v1` for *ReplicaSet*
2. *selector* - required to determine which pods to manage. Defined by `matchLabels`, which can also capture pods created before the *ReplicaSet* if they match the criteria.

To verify *ReplicaSet* creation, use:
```
kubectl get replicaset
```

Scaling a *ReplicaSet* invloves adjusting the number of pod replicas. There are two methods to achieve this:
1. Update the definition file - modify the `replicas` value in your definition file and update *ReplicaSet* with:
```
kubectl replace -f replicaset-definition.yaml
```
2. Scale directly from the command line
```
kubectl scale --replicas=6 -f replicaset-definition.yaml
```