*Services* - allow different sets of *Pods* to interact with each other. For instance, you can expose your front-end to end users and enable back-end components to interact efficiently.

Types of services:
- *NodePort* - maps a port on the node to a port on a *Pod*
- *ClusterIP* - creates a virtual IP for internal communication between services (for example: connecting front-end to back-end servers)
- *LoadBalancer* - provisions an external load balancer to distribute traffic across multiple *Pods*

To verify services details, use:
```
kubectl get services
```

**NodePort** - three key ports to consider:
1. *targetPort* - the port on the *Pod* where the application listens 
2. *port* - the virtual port on the service within the cluster
3. *nodePort* - external port on the Kubernetes node
If you omit `targetPort`, it defaults to the same value as `port`.
If `nodePort` isn't provided, Kubernetes automatically assigns one.
To connect the service to specific *Pods*, a `selector` is used.

**ClusterIP** - streamlines connectivity within an application by providing a stable interface for pod-to-pod communication. Allows other pods to access service without worrying about individuals IPs.

**LoadBalancer** - only functions as intended on supported cloud environments. In unsupported settings, behaves like *NodePort* by exposing the service on a high port without providing external load balancing.