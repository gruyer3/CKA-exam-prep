When you use `kubectl apply` command, it compares three sources:
1. The local configuration file
2. The live object configuration stored on the Kubernetes cluster
3. The last applied configuration stored as an annotation on the live object

Command may be used for:
- Resource initial creation
- Configuration updates
- Removing fields from live configuration