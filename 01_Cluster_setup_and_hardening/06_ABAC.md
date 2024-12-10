# Attribute based access control (ABAC)

Json object per line (JSONL) format:
```
cat <<EOF > /etc/kubernetes/abac/abac-policy.jsonl
{"apiVersion": "abac.authorization.kubernetes.io/v1beta1", "kind": "Policy", "spec": {"user": "system:serviceaccount:default:john", "namespace": "default", "resource": "pods", "apiGroup": "*" , "readonly": true}}
EOF
```

This policy grants read-only access to the pods resource in the default namespace for the service account john

Enable ABAC in kube-api-server:
Edit the API server manifest file (usually located at /etc/kubernetes/manifests/kube-apiserver.yaml) and add the following flags under the command section:
```
# /etc/kubernetes/manifests/kube-apiserver.yaml

- --authorization-mode=Node,RBAC,ABAC
- --authorization-policy-file=/etc/kubernetes/abac/abac-policy.jsonl
```
Add volume mounts to the API server pod spec:
```
# /etc/kubernetes/manifests/kube-apiserver.yaml

volumeMounts:
# Other volume mounts...
- name: abac-policy
  mountPath: /etc/kubernetes/abac
  readOnly: true

volumes:
# Other volumes...
- name: abac-policy
  hostPath:
    path: /etc/kubernetes/abac
    type: DirectoryOrCreate
```
The kube-apiserver will automatically restart sometime after the manifest file is updated.
To check the logs, run ```cat /var/log/containers/kube-apiserver-*```