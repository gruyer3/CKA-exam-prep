**Node affinity** enables you to specify detailed rules for pod placement based on node labels.

Node affinity configuration:
- The *affinity* key under *spec* introduces the *nodeAffinity* configuration.
- *requiredDuringSchedulingIgnoredDuringExecution* - indicates that the scheduler must place the pod on a node meeting the criteria. Once the pod is running, any changes to node labels are ignored.
- *nodeSelectorTerms* - array contains one or more *matchExpressions*. Each expression specifies a label key, an operator, and a list of values.
- *NotIn* operator avoid placing a pod on nodes with specific labels.
- *Exists* operator verify the presence of a label without checking for specific values.

There are two primary scheduling behaviors for node affinity:
- *Required During Scheduling, Ignored During Execution*:
    - The pod is scheduled only on nodes that fully satisfy the affinity rules.
    - Once running, changes to node labels do not impact the pod.
- *Preferred During Scheduling, Ignored During Execution*:
    - The scheduler prefers nodes that meet the affinity rules but will place the pod on another node if no matching nodes are available.