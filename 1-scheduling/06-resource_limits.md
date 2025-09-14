**Resource limits** define the minimum CPU and memory a container is guaranteed when scheduled. Specifying a request, for instance, of 1 CPU and 1 GB memory in a pod definition ensures that the pod will only be scheduled on a node that can provide these minimum resources.

It is possible to use fractional CPU values. For example, 0.1 CPU is equivalent to 100m (where "m" denotes milli, meaning 0.001 of a CPU).

By default, a container in a pod can consume all the available resources on its node if no limits are set. Usage of resources can be restricted by defining resource limits, such as 1 vCPU, prevents the container from using more than that allocation. Note that while CPU usage is throttled when a pod reaches its limit, memory usage is not. If a pod exceedes its memory limit, it may be terminaed due to OOM error.

Kubernetes does not enforce CPU or memory requests and limits.

Example scenarios:

1. _No Requests or Limtis_ - container can utilize all available CPU, potentially starving other pods
2. _Limits specified without Requests_ - Kubernetes assumes the request value is equal to the limit
3. _Both Requests and Limits defined_ - container is guaranteed its requested amount but can use additional CPU up to its definted limit
4. _Requests defined without Limits_ - container is guaranteed its requested CPU value, with access to additional cycles if available, which allows for efficient utilization of idle resources

Similar configurations apply for memory:

- Without any resource configuration, a single pod may monopolize node memory
- When only limits are specified, Kubernetes sets the memory request equal to the limit
- With both requests and limtis, the pod is allocated a guaranteed memory amount and can burst up to the limit
- Only specifying requests guarantees the pod a bse amount of memory but might let it consume more, potentially leading to termination if memory usage become excessive

To ensure that every pod in a namespace receives default resource settings, you can define a LimitRange. LimitRanges are namespace-level objects that automatically assign default resource values to containers that do not specify them.
