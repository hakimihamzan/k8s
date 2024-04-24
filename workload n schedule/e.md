Create a single Pod named service-ready of image nginx:1.16.1-alpine . Configure LivenessProbe which simply executes command true .

Also configure a ReadinessProbe which checks if the url http://localhost:80 is reachable, you can use wget -T2 -O- http://localhost:80 for this. Start the Pod and confirm it is ready.

apiVersion: v1
kind: Pod
metadata:
  name: service-ready
spec:
  containers:
  - name: nginx
    image: nginx:1.16.1-alpine
    livenessProbe:
      exec:
        command: ['true']
      initialDelaySeconds: 5
      periodSeconds: 5
    readinessProbe:
      exec:
        command:
        - /bin/sh
        - -c
        - "wget -T2 -O- http://localhost:80"
      initialDelaySeconds: 5
      periodSeconds: 5