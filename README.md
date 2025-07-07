# K8s-CKAD

```Bash
k describe pod <Pod name>
```
```Bash
k describe pod <Pod name>
```
```Bash
k get pods
```
```Bash
#create a new resource from a definition file
k apply -f </path/to/file/file.yaml>
```
```Bash
#List all available replicasets
k get replicasets
```
```Bash
#Delete a replicaSets
k delete replicaset <Name of the replicaSet>
```
```Bash
#Create new pod with image
kubectl run my-nginx --image=nginx
```
```Bash
# extract the definition to a file
kubectl get pod <pod-name> -o yaml > pod-definition.yaml
```
```Bash
# Modify the properties of the pod
kubectl edit pod <pod-name>
```
