# Commands

Get pod information
`kubectl get pod -o wide`

Create Object by file
`kubectl create -f <yaml_template>`

**BasicPod YAML**:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: basicpod
  labels:
    type: webserver
spec:
  containers:
    - name: webcont
      image: nginx
      ports:
        - containerPort: 80
```

**BasicService YAML**:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: basicservice
spec:
  selector:
    type: webserver
  type: NodePort # assigned by k8s its literally the port of the host machine
    ports:
      - protocol: TCP
        port: 5001 # <-- Service port where the service is listening
        targetPort: 5000 # where the traffic is going to be forwarded inside the container
```

**NOTE IMPORTANT!!!**: if you want to expose your GCP VM or AWS EC2 server the right number to apply on your
firewall rules is the `<ExternalPort>` value that could be listed using `kubectl get service -o wide`

Default NodePort ranges used by services **30000-32767**

```bash
NAME                   TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)                 AGE   SELECTOR
service/basicservice   NodePort    10.106.27.161   <none>        80:<ExternalPort>/TCP   53m   type=webserver
```
