k run ubuntu-pod --image=ubuntu --labels="app=os"

apiVersion: v1
kind: Service
metadata:
  name: ubuntu-service
spec:
  selector:
    app: os
  ports:
    - protocol: TCP
      port: 80
      targetPort: 8080