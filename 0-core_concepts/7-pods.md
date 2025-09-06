*Pod* - represents a single instance of an application and is the smallest deployable unit in Kubernetes. Running two instances in separate pods allows the load to be shared across the node or even across multiple nodes.

Scaling an application in Kubernetes involves increasing or decreasing the number of pods, not the number of containers within a single pod.

Typically, each pod hosts a single container running your main application. However, a pod can also contain multiple containers, which are usually complementary rather than redundant. 

Common method to deploy pods is using the `kubectl run` command.
```
kubectl run nginx --image nginx
```
Once deployed, pod's status may be verified with the command below:
```
kubectl get pods
```

Pods may also be defined with YAML files. Every Kubernetes definition file must include the following four fields:
```
apiVersion:
kind:
metadata:
spec:
```
1. *apiVersion* - indicates the version of the Kubernetes API you're using. For a *Pod*, set `apiVersion: v1`. Depending on the object you define, you might need different versions.
2. *kind* - specifies the type of object being created. Since we're creating a *Pod*, in that case it'll be defined as `kind: Pod` but other objects might include ReplicaSet, Deployment or Service.
3. *metadata* - provides details about the object, including its name and labels. Is represented as a dictionary.
```
metadata:
    name: myapp-pod
    labels:
        app: myapp
```
4. *spec* - provides specific configuration details for the object. For a Pod, this is where containers are defined. Since a *Pod* can run multiple containers, `containers` field is an array.
```
spec:
  containers:
    - name: nginx-container
      image: nginx
```

Use the following command to create a *Pod* from a definition file:
```
kubectl create -f *<file-name>*.yaml
```

To view detailed information about the *Pod*, run:
```
kubectl describe pod *<pod-name>*
```
