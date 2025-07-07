# K8s-CKAD

## Pod
Erstellt einen neuen Pod aus einem Image
```Bash
k describe pod <Pod name>
```
Listet alle Pods im aktuellen Namespace auf
```Bash 
k get pods
```
Create a new resource from a definition file
```Bash
k apply -f </path/to/file/file.yaml>
```
Modify the properties of the pod
```Bash
kubectl edit pod <pod-name>
```
## ReplicaSets
List all available replicasets
```Bash
k get replicasets
```
Delete a replicaSets
```Bash
k delete replicaset <Name of the replicaSet>
```
Create new pod with image
```Bash
kubectl run my-nginx --image=nginx
```
Extract the definition to a file
```Bash
kubectl get pod <pod-name> -o yaml > pod-definition.yaml
```
creates the Kubernetes objects (like Pods, Services, or Deployments) defined within it
```Bash
k create -f <file>.yml
```
