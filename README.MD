# Tomer Cohen Answers for K8s project

1.Deploy a pod named nginx-pod using the nginx:alpine image.
# 'kubectl run nginx-pod-tomer --image nginx:1.23.1-alpine'

2.Deploy a messaging pod using the redis:alpine image with the labels set to tier=msg. 
# 'kubectl run messaging --image redis:7-alpine --labels tier=msg'

3.Create a namespace named apx-x998-yourname
# 'kubectl create namespace apx-x998-tomer'

4.Get the list of nodes in JSON format and store it in a file at /tmp/nodes-yourname
# 'kubectl get nodes -o=jsonpath='{.items[*].metadata.name}' > nodes-tomer.json'

5.Create a service messaging-service to expose the messaging application within the cluster on port 6379.
# 'kubectl create service clusterip messaging-service --tcp 6379:6379'
# 'kubectl label service messaging-service tier=msg'

6.Create a service messaging-service to expose the messaging application within the cluster on port 6379.
# look at messaging-service.yaml file'

7.Create a deployment named hr-web-app using the image kodekloud/webapp-color with 2 replicas
# 'kubectl create deployment hr-web-app --image kodekloud/webapp-color  --replicas 2 '

8.Create a static pod named static-busybox on the master node that uses the busybox image and the command sleep 1000
# 'look at static-pod.manifest file'

9.Create a POD in the finance-yourname namespace named temp-bus with the image redis:alpine 
# 'kubectl create namespace finance-tomer'
# 'kubectl run temp-bus  --image redis:7-alpine --namespace finance-tomer'
  
10.Create a Persistent Volume with the given specification 
# 'look at pv-volume.yaml file'

11.Create a Pod called redis-storage-yourname with image: redis:alpine with a Volume of type emptyDir that lasts for the life of the Pod. specs:.
# 'look at redis-storage-tomer-pod.yaml file'

12.Create this pod and attached it a persistent volume called pv-1 
# 'look at pv-1.yaml file'
# 'look at pvc-1.yaml file'
# 'look at use-pv.yaml file'

13.Create a new deployment called nginx-deploy, with image nginx:1.16 and 1 replica. 
# 'kubectl create deployment nginx-deploy --image nginx:1.16 --replicas 1'
# 'kubectl set image deployment nginx-deploy nginx=nginx:1.17'
# 'kubectl get rs'

14.Create an nginx pod called nginx-resolver using image nginx
# 'kubectl run nginx-resolve --image nginx:1.23.1-alpine --labels app=resolver --port 80'
# 'kubectl create service clusterip nginx-resolver-servic --tcp 80:80'
# 'kubectl label service nginx-resolver-servic app=resolver'
# 'kubectl get pods -l app=resolver'
# 'kubectl run busybox-resolve --image busybox:1.2 --labels app=resolver'
# 'kubectl get ep'
# 'kubectl exec --stdin --tty usybox-resolve -- /bin/bash'
# 'nslookup 'Service Endpoint IP'

15.Create a static pod on node01 called nginx-critical with image ngin
# 'add the folowwing line in the static-pod.yaml --> restartPolicy: OnFailure'

16.Create a pod called multi-pod with two container
# ' look at multi-pod.yaml'

### Pod Design Questions ###
1. 'kubectl get pods -l label=value'
2. 'kubectl create deployment test --image nginx:1.23.1-alpine  --replicas 2 --labels env=prod'
   'kubectl create deployment test2 --image nginx:1.23.1-alpine  --replicas 3 --labels env=dev'
3. 'kubectl get pods -l env=prod,env=dev'
4 + 5. 'kubectl get pods -l env=dev > dev-pods.txt
6 + 7. 'kubectl get pods -l env=prod > prod-pods.txt
8. 'kubectl get pods -A | grep 'env'
9. 'kubectl get pods -l env=prod,env=dev'
10. 'kubectl get pods -l env=prod,env=dev' > labels-pods.txt
11. 'kubectl label pod ('pod-name') env=uat'
12. 'kubectl label pod ('pod-name') env-
13. 'kubectl label deployment test test2 app=nginx'
    'kubectl get deployment -l app=ngnix'
14. 'kubectl get nodes -A'
15. 'kubectl label node minikube nodeName=nginxnode'
16. create new pod with Yaml and add below containers sections --> nodeName: nginxnode
17. 'kubectl describe pod ('pode-name')'

Deployments:

1. a. 'kubectl create deploy webapp --image=nginx --dry-run -o yaml > webapp.yaml'
   b. 'kubectl edit deployment webapp' --> change the replicas from 1 to 5
2. 'kubectl rollout status deployment/webapp'
3. 'kubectl get rs'
4. 'kubectl get rs -o yaml'
5. kubectl delete deployment webapp'
6. a. 'kubectl create deploy webapp --image=nginx:1.17.1 --dry-run -o yaml > webapp.yaml'
   b.  edit the yaml and add below containers --> ports: - containerPort: 80
7. 'kubectl set image deployment nginx-deploy nginx=nginx:1.17.4'
8. 'kubectl get rs'
9. 'kubectl rollout undo deployment/webapp --to-revision=1'
10. a. 'kubectl set image deployment webapp nginx=nginx:1.100'
    b. 'kubectl rollout undo deployment/webapp --to-revision=1'
    e. 'kubectl set image deployment webapp nginx=nginx:latest'
11. 'kubectl autoscale deployment webapp --cpu-percent=85 --min=1 --max=10'
    'kubectl get hpa'
13. 'kubectl delete hpa webapp-hpa'
    'kubectl delete deployment webapp'
14. 'look at hello-job.yaml'

Config Map:
1 + 2. 'kubectl create configmap conf-map --from-file ./config.txt --dry-run=client -o yaml'\
3. 'look into files: config.txt + conf-map.yaml + nginx-pod-confmap.yaml'
