*Deployments* - offer advanced features that enable you to:
- deploy multiple instances of an application to ensure high availability and load balancing
- seamlessly perform rolling updates for images so that instances update gradually, reducing downtime
- quickly roll back to a previous version if upgrade fails unexpectedly
- pause and resume deployments, allowing to implement coordinated changes such as scaling, version updates or resource modifications

Once created, deployment automatically creates an associated resources such as *ReplicaSet*, *Pod* etc.

To view all the created objects, use following command:
```
kubectl get all
```
