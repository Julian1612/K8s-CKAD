# K8s-CKAD
creates the Kubernetes objects (like Pods, Services, or Deployments) defined within it
```Bash
k create -f <file>.yml
```
Create a new resource from a definition file
```Bash
k apply -f </path/to/file/file.yaml>
```

## Pod
Erstellt einen neuen Pod aus einem Image
```Bash
k describe pod <Pod name>
```
Listet alle Pods im aktuellen Namespace auf
```Bash 
k get pods
```
Modify the properties of the pod
```Bash
kubectl edit pod <pod-name>
```
Create new pod with image
```Bash
kubectl run my-nginx --image=nginx
kubectl run nginx --image=nginx --dry-run=client -o yaml
```
Extract the definition to a file
```Bash
kubectl get pod <pod-name> -o yaml > pod-definition.yaml
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
## Deployment

```Bash
kubectl create deployment --image=nginx nginx
```
Generate Deployment YAML file (-o yaml). Don't create it(--dry-run)
```Bash
kubectl create deployment --image=nginx nginx --dry-run -o yaml
```
```Bash
kubectl create deployment nginx --image=nginx --replicas=4
kubectl create deployment nginx --image=nginx--dry-run=client -o yaml > nginx-deployment.yaml
```
## Service
```Bash
kubectl expose pod redis --port=6379 --name redis-service --dry-run=client -o yaml
```
```Bash
kubectl create service clusterip redis --tcp=6379:6379 --dry-run=client -o yaml
```
```Bash
kubectl create service nodeport nginx --tcp=80:80 --node-port=30080 --dry-run=client -o yaml
```


##Imerative Commands
as soon as the command is run, the resource will be created. If you simply want to test your command, use the --dry-run=client option. This will not create the resource. Instead, tell you whether the resource can be created and if your command is right.
```Bash
--dry-run
--dry-run=client
```
will output the resource definition in YAML format on the screen.
```Bash
-o yaml
```
```Bash
kubectl run nginx --image=nginx --dry-run=client -o yaml > nginx-pod.yaml
```

