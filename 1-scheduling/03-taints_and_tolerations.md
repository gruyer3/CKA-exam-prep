**Taint** is applied to a node (the repellent) to repel pods unless they have a matching **toleration**. This ensures that only intended pods can run on tainted nodes.

Two factors determine whether a pod can run on a node:
1. The taint applied on the node
2. The pod's toleration for that taint

**Taints** and **tolerations** are used solely for scheduling control, not security. 

There are three taint effects:
- *NoSchedule* - pods that do not tolerate the taint will not be scheduled on the node
- *PreferNoSchedule* - scheduler tries to avoid placing non-tolerating pods on the node, but it is not strictly enforced
- *NoExecute* - new pods without a matching toleration will not be scheduled and existing pods will be evicted from the node

To taint a node, use the following command:
```
kubectl taint nodes node-name key=value:taint-effect
```

To allow a specific pod to run on a tainted node, add a *toleration* to the pod's manifest.
```
spec:
  tolerations:
    - key: "app"
      operator: "Equal"
      value: "blue"
      effect: "NoSchedule"
```

Using the *NoExecute* taint effect has a more immediate impact. In an initially untainted cluster, all pods schedule normally, but once the taint is applied:
- pods without a matching toleration will be evicted from node if already running or prevented from being scheduled
- pods with the correct toleration continue to run on the node

Taints and tolerations are used to ensure that pods are not accidentally scheduled on nodes that should run only specific workloads, but they do not guarantee that a pod will run on a particular node. For node-specific scheduling, consider using node affinity.

By default, Kubernetes applies a taint to master nodes to prevent workload pods from being scheduled there. To check the taint on a master node, use the following command:
```
kubectl describe node kubemaster | grep Taint
```
