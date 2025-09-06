*Controller manager* - component in Kubernetes reponsible for managing a variety of controllers within your cluster. Each controller is handling a specific responsibility, for example: one controller might monitor the health of nodes, while another ensures that the desired number of pods is always running.

*Node controller* - checks node statuses every five seconds through the Kube API Server. If a node stops sending heartbeats, it is not immediately marked as unreachable; instead, there is a grace period of 40 seconds followed by an additional five minutes for potential recovery before its pods are rescheduled onto a healthy mode. 

*Replication controller* - ensures that the specified number of pods is maintained by creating new pods when needed which reinforces the resilience and reliability of your cluster.

All core Kubernetes constructs rely on these controllers.