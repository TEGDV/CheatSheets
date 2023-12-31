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
  type: NodePort
    ports:
      - protocol: TCP
        port: 80
```
