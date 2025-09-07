**Labels** and **selectors** offer a systematic approach to categorizing items.
To apply labels to a Kubernetes objects such as a Pod, include *labels* section under the *metadata* field in its definition file.

When creating a **ReplicaSet** to manage three Pods, you first label the Pod definitions and then use a selector in the **ReplicaSet** definition to ensure the correct Pods are grouped together.
**ReplicaSet** definition includes labels in two areas:
- metadata
- template
By setting the *selector* field in the **ReplicaSet** specification to match the labels defined on the Pods, you ensure that the **ReplicaSet** manages the intended Pods.

**Annotations** differ from labels and selector as they're used to store additional metadata that is not intended for selection. This metadata might include details such as tool versions, build information or contact information. 