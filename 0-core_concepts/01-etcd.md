*etcd* - distributed key-value store that maintains configuration data, stale information and metadata for your Kubernetes cluster. Every object - nodes, pods, configurations, secrets, accounts, roles and role bindings - is stored within etcd. 

When you run a command like `kubectl get`, the data is retrieved from this data store.
Any changes made to the cluster are first recorded in *etcd*.