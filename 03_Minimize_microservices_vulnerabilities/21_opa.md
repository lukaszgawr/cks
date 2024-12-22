# Open Policy Agent (OPA)

Not taking k8s into consideration yet we need to run a server:
![](../images/21_opa_1.png)
After OPA service is running we need to load policy:
![](../images/21_opa_2.png)
and apps can now use it:
![](../images/21_opa_3.png)

## Policy testing
![](../images/21_opa_4.png)

## OPA in Kubernetes
### kube-mgmt
kube-mgmt manages policies / data of Open Policy Agent instances in Kubernetes.
  
kube-mgmt is uded to:  
* Load policies and/or static data into OPA instance from ConfigMap.
* Replicate Kubernetes resources including CustomResourceDefinitions (CRDs) into OPA instance.

### Policies and data loading

`kube-mgmt` automatically discovers policies and JSON data
stored in `ConfigMaps` in Kubernetes and loads them into OPA.

`kube-mgmt` assumes a `ConfigMap` contains policy or JSON data if the `ConfigMap` is:

- Created in a namespace listed in the `--namespaces` option.
  If you specify `--namespaces=*` then `kube-mgmt` will look for policies in ALL namespaces.
- Labelled with `openpolicyagent.org/policy=rego` for policies
- Labelled with `openpolicyagent.org/data=opa` for JSON data

Policies or data discovery and loading can be disabled using `--enable-policy=false` or `--enable-data=false` flags respectively.

Label names and their values can be configured using `--policy-label`, `--policy-value`, `--data-label`, `--data-value` CLI options.

When a `ConfigMap` has been successfully loaded into OPA,
the `openpolicyagent.org/kube-mgmt-status` annotation is set to `{"status": "ok"}`.

If loading fails for some reason (e.g., because of a parse error), the
`openpolicyagent.org/kube-mgmt-status` annotation is set to `{"status": "error", "error": ...}`
where the `error` field contains details about the failure.

Data loaded out of ConfigMaps is laid out as follows:

```
<namespace>/<name>/<key>
```

For example, if the following ConfigMap was created:

```yaml
kind: ConfigMap
apiVersion: v1
metadata:
  name: hello-data
  namespace: opa
  labels:
    openpolicyagent.org/data: opa
data:
  x.json: |
    {"a": [1,2,3,4]}
```
Note: "x.json" may be any key.

You could refer to the data inside your policies as follows:

```rego
data.opa["hello-data"]["x.json"].a[0]  # evaluates to 1
```



## OPA Gatekeeper
![](../images/21_opa_5.png)
Installation - install according to instruction: https://open-policy-agent.github.io/gatekeeper/website/docs/install/

after installed make sure all components are running:
![](../images/21_opa_6.png)
![](../images/21_opa_7.png)
![](../images/21_opa_8.png)
![](../images/21_opa_9.png)
![](../images/21_opa_10.png)
But label is still hardcoded in rego (we will modify it later).

How to make SystemRequiredLabel kind ?
![](../images/21_opa_11.png)

Now we can change label in rego to parameter:
![](../images/21_opa_12.png)
![](../images/21_opa_13.png)
![](../images/21_opa_14.png)
