**DeamonSets** ensure that exactly one copy of a pod runs on every node within a cluster. When a new node is added, the **DeamonSet** automatically deploys the pod on the new node. Likewise, when the node is removed, the corresponding pod is also removed.

**DeamonSets** are useful in scenarios where you need to run background services or agents on every node. Some of the use cases include:

- deploy monitoring tools or log collectors across every node to ensure comprehensive cluster-wide visibility without manual intervention
- deploy critical components, such as kube-proxy, which Kubernetes require on every worker node
- ensure consitent deployment of networking agents like those used in VNet or weave-net across all nodes

Verify the **DeamonSet's** creation with:

```
kubectl get deamonsets
```

For more detailed information, use:

```
kubectl describe deamonset <deamonset-name>
```
