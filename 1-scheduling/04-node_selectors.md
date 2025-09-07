**Node selectors** help align your pod deployments with the underlying hardware characteristics of your nodes, enhancing performance and resource management.

To ensure that a pod is restricted to run on a specific node, you can modify the pod's definition file using node selectors.
```
spec:
  nodeSelector:
    size: Large
```

Before deploying your pod, you must label your node so that it can be recognized by the selector.
```
kubectl label nodes node-1 size=Large
```

While node selectors are ideal for simple scenarios involving a single label, they come with certain limitations. For instance, if you need to schedule a pod on a node that is either large or medium, or on any node that is not labeled as small, a basic node selector may not suffice. In these cases, consider using node affinity and anti-affinity features.