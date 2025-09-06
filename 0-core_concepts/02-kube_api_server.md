*Kube API Server* - acts as the central management component within a cluster by handling requests from `kubectl`, validating and authenticating them, interfacing with the *etcd* data store and coordinating with other system components.

When you execute a command like:
```
kubectl get nodes
```
the utility sends a request to the API server which then processes this request by authenticating the user, validating the request, fetching data from the *etcd* cluster and replying wht the desired information.

When a direct API POST request is made to create a pod, the API Server:
1. Authenticates and validates the request
2. Constructs a pod object and updates the *etcd* store
3. Notifies the requester that the pod has been created

