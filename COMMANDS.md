Here’s a clean, practical Kubernetes command sheet covering everything you’ve learned so far (Pods, Deployments, Services, ConfigMaps, Secrets, and basic debugging).

### 1. Cluster & Context

### Check current cluster

`kubectl config current-context`

### List all contexts

`kubectl config get-contexts`

### List namespaces

`kubectl get ns`

### List nodes

`kubectl get nodes`

### Detailed node info

`kubectl get nodes -o wide`

### 2. See Resources

### Everything in current namespace

`kubectl get all`

### Everything in all namespaces

`kubectl get all -A`

### Pods

`kubectl get pods`

### Pods with IP and node

`kubectl get pods -o wide`

### Pods with labels

`kubectl get pods --show-labels`

### Watch pods live

`kubectl get pods -w`

### Deployments

`kubectl get deploy`

### Services

`kubectl get svc`

### ConfigMaps

`kubectl get configmaps`

### Secrets

`kubectl get secrets`

### 3. Create Resources

### Create deployment

`kubectl create deployment nginx --image=nginx --replicas=2`

### Expose deployment as service

`kubectl expose deployment nginx --port=80 --target-port=80 --type=ClusterIP`

### Apply YAML file

`kubectl apply -f file.yaml`

### 4. Inspect Resources

### Describe pod

`kubectl describe pod <pod-name>`

### Describe deployment

`kubectl describe deployment <deployment-name>`

### Describe service

`kubectl describe service <service-name>`

### Describe configmap

`kubectl describe configmap <name>`

### Describe secret

`kubectl describe secret <name>`

### 5. Logs & Shell Access

### View logs

`kubectl logs <pod-name>`

### Follow logs

`kubectl logs -f <pod-name>`

### Open shell inside pod

`kubectl exec -it <pod-name> -- sh`

### Run a command in pod

`kubectl exec <pod-name> -- env`

### 6. Scaling & Updates

### Scale deployment

`kubectl scale deployment nginx --replicas=5`

### Update image

`kubectl set image deployment/nginx nginx=nginx:latest`

### Restart deployment

`kubectl rollout restart deployment nginx`

### Check rollout status

`kubectl rollout status deployment nginx`

### 7. Delete Resources

### Delete pod

`kubectl delete pod <pod-name>`

### Delete deployment

`kubectl delete deployment nginx`

### Delete service

`kubectl delete service nginx`

### Delete from YAML

`kubectl delete -f file.yaml`

### 8. Service & Networking

### See service endpoints (very important)

`kubectl get endpoints nginx`

### Port-forward service to local machine

`kubectl port-forward service/nginx 8080:80`

### Port-forward pod

`kubectl port-forward pod/<pod-name> 8080:80`

### 9. ConfigMaps

### Create from literals

`kubectl create configmap app-config --from-literal=APP_ENV=dev --from-literal=LOG_LEVEL=debug`

### View YAML

`kubectl get configmap app-config -o yaml`

### 10. Secrets

### Create secret

`kubectl create secret generic db-secret --from-literal=username=admin --from-literal=password=supersecret`

### View YAML

`kubectl get secret db-secret -o yaml`

### Decode a value

`echo c3VwZXJzZWNyZXQ= | base64 -d`

### 11. Useful Debugging Commands

### What is failing?

`kubectl get pods`

### Why is it failing?

`kubectl describe pod <pod-name>`

### What are the logs?

`kubectl logs <pod-name>`

### Is the service routing traffic?

`kubectl get endpoints <service-name>`

### Which labels exist?

`kubectl get pods --show-labels`

### 12. The 10 Commands You’ll Use 80% of the Time

```bash
kubectl get pods 
kubectl get pods -o wide 
kubectl get svc 
kubectl get deploy 
kubectl describe pod <pod> 
kubectl logs <pod> 
kubectl exec -it <pod> -- sh 
kubectl scale deployment <name> --replicas=3 
kubectl get endpoints <service> 
kubectl get all
```