### Pull an Image from a Private Registry

*Step 1:* Create this Secret, naming it `regcred`:
```
kubectl create secret docker-registry regcred --docker-server=<your-registry-server> --docker-username=<your-name> --docker-password=<your-pword> --docker-email=<your-email>
```

*Step 2:* Specify the secret in the .yaml file
```
      imagePullSecrets:
        - name: regcred
```
[more details](https://kubernetes.io/docs/tasks/configure-pod-container/pull-image-private-registry/)
