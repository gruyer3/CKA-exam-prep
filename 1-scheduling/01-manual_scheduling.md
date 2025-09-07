Every pod definition includes a field called *nodeName*, which is left unset by default.
The Kubernetes scheduler automatically scans for pods without a *nodeName* and selects an appropiate node by updating this field and creating a binding object.

To manually assign a pod to specific node during creation, populate the *nodeName* field in the manifest.
```
spec:
  nodeName: node02
```

If pod is already running and you need to change its node assignment, you cannot modify its *nodeName* directly but you can create a binding object that mimics the scheduler behavior.
1. Create a binding object that specifies the target node
2. The original pod definition remains unchanged
3. Covert the YAML binding to JSON and send a POST request to the pod's binding API using curl
```
curl --header "Content-Type: application/json" --request POST --data @binding.json http://$SERVER/api/v1/namespaces/default/pods/nginx/binding
```