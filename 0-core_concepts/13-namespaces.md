*Namespaces* - allow to group and manage resources differently based on their context and intended use. By default, when objects are created they are placed within a specific namespace. The default namespace is automatically created during the Kubernetes cluster setup. Additionally, several system namespaces are created at startup:
- *kube-system* - contains core system components like network services and DNS, segregated from user operations to prevent accidental changes
- *kube-public* - intended for resources that need to be publicly accessible accross users

Namespaces allow you to set distinct policies and resource limits for different environments. This isolation prevents one namespace from interfering with another.

To list all pods in the default namespace, use:
```
kubectl get pods
```
To list pods within the *kube-system* namespace, use:
```
kubectl get pods --namespace=kube-system
```
To list pods from all namespaces, use:
```
kubectl get pods --all-namespaces
```
To create the pod in different namespace using a definition file, use:
```
kubectl create -f <file-name>.yaml --namespace=<namespace>
```

Namespace may be created directly from the terminal with:
```
kubectl create namespace <name>
```

You may set up default *namespace* for your context by using:
```
kubectl config set-context $(kubectl config current-context) --namespace=<name>
```