Labels enable controllers, such as *ReplicaSets* to identify and manage the appropriate pods within a large cluster. For example, assign a label to each pod, then use a selector to target those pods.
```
selector:
  matchLabels:
    tier: front-end
```
The pod definition should similarly include the label:
```
metadata:
  name: myapp-pod
  labels:
    tier: front-end
```
