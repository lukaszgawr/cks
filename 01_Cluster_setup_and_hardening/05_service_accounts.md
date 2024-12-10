# Service Accounts

## Create SA and link to secret with token

```yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  name: my-service-account
  namespace: default
secrets:
  - name: my-service-account-token
---
apiVersion: v1
kind: Secret
metadata:
  name: my-service-account-token
  namespace: default
  annotations:
    kubernetes.io/service-account.name: "my-service-account"
type: kubernetes.io/service-account-token
```
```
controlplane ~ ➜  k describe sa my-service-account
Name:                my-service-account
Namespace:           default
Labels:              <none>
Annotations:         <none>
Image pull secrets:  <none>
Mountable secrets:   my-service-account-token
Tokens:              my-service-account-token
Events:              <none>
```
## Use this SA with token to talk to API server

RBAC have to be created first of course for SA.

Get the API Server Endpoint:  
```APISERVER=$(kubectl config view --minify -o jsonpath='{.clusters[0].cluster.server}')```  
Get the CA Certificate:  
```CACERT=$(kubectl config view --minify -o jsonpath='{.clusters[0].cluster.certificate-authority}')```  
If the CA certificate is embedded in your kubeconfig, extract it:  
```kubectl config view --raw -o jsonpath='{.clusters[0].cluster.certificate-authority-data}' | base64 --decode > ca.crt```   
Retrieve the Token:  
```SECRET_NAME=$(kubectl get serviceaccount my-service-account -o jsonpath='{.secrets[0].name}')```
  
```TOKEN=$(kubectl get secret $SECRET_NAME -o jsonpath='{.data.token}' | base64 --decode)```

Use curl to Access the API Server:

```curl --cacert ca.crt -H "Authorization: Bearer $TOKEN" "$APISERVER/api/v1/namespaces/default/pods"```