*Replication controller* - ensures high availability by creating and maintaining the desired number of pod replicas. Even if you intend to run a single pod, a replication controller adds redundancy by creating a replacement if the pod fails.

To create a *replication controller* write a configuration file with these four sections:
1. *apiVersion* - for a replication controller, use `v1`
2. *kind* - set this to `ReplicationController`
3. *metadata* - provide a name (e.g. `myapp`) and include labels such as `app` and `type`
4. *spec* - defines the desired number of replicas with the `replicas` key and includes `template` section which serves as the blueprint for creating the *pods*.

Once the definition file is ready, create *replication controller* by using the following command:
```
kubectl create -f *<file-name>*.yaml
```
To view the *replication controller* and its pods, run these commands:
```
kubectl get replicationcontroller
kubectl get pods
```