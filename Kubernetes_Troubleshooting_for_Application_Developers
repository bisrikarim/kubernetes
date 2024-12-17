# kubectl get:
- debug with json path

# kubectl describe:
- k describe nodes node1

# kubectl get events:
- ex: k get events -n monitoring

# kubectl logs
- ex: k logs multi-container-pod --all-containers
k get pod multi-containers-pod -o jsonpath='{.spec.containers}'  // the pod contains two containers
=> get logs for the first one : k get logs multi-container-pod -c nginx-container
=> get logs for the second one : k get logs multi-container-pod -c cron-logger

# kubectl logs --label => get logs of different objects that shars the same labels:
- ex: k get deployments.apps -n uat notes-app-deployment -o yaml | grep labels -A5
k logs -n uat -l app=notes-app

# kubectl logs --timestamp
- ex: k logs -n uat notes-app-deployment-fdfsd744-fdsfsd --timestamp
- ex: k logs logs-generator --since=5s

# kubectl logs --follow => real time logs
- ex: 
# kubectl run logs-generator \
  --image=gcr.io/google_containers/logs-generator:v0.1.1 \
  --env "LOGS_GENERATOR_LINES_TOTAL=1000" \
  --env "LOGS_GENERATOR_DURATION=5m"
# k logs logs-generator --follow


# kubectl exec
- ex: k exec logs-generator -- ls
- ex: k exec logs-generator -it -- /bin/bash

# kubectl port-forward (for debuging purposes)
- ex: k port-forward svc/nginx-service 8000:80 ==> 8000 is the local port
      http://localhost:8000 // or : curl localhost:8000


# kubectl auth can-i => to check roles and rolebinding in rbac
very useful when we have a lot of sa, roles, rolebindings ...

- ex: $ kubectl auth can-i [ create - list - delete - get - watch -  ... ] [ pods - services - ... ]

- ex: $ k auth whoami

- ex: $ k auth can-i get pods --as=jane
      => yes   ==> So jane can get pods on default namespace

- ex: $ k auth can-i get pods --as=jane --v=10
      => yes   ==> So jane can get pods on default namespace with more verbosity displaying

- ex: $ k auth can-i delete pods --as=system:serviceaccount:default:default
      => no      ====> the sa default cannot delete pods on default namespace

- ex: $ k auth can-i list pods --as=system:serviceaccount:default:default
      => no      ====> the sa default cannot delete pods on default namespace

# kubectl top
- ex: k top nodes
- ex: k top pods


# kubectl explain:
- ex: k explain pods 
- ex: k explain pods.spec
- ex: k explain pods.spec.securityContext --recursive

# kubectl diff => diff between the ressource deployed in cluster vs why i defined in current manifests files : 
- ex: 
1- cat redis.yml
2- k get deploy -n redis
3- k diff -f redis.yml


