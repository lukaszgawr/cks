# Admission controllers

## Default admission controllers
E.g. namespace exists - to check for namespaces:
![](../images/18_admission_controllers_1.png)

To check what are enabled admission controllers:
![](../images/18_admission_controllers_2.png)

## Enabling and disabling admission controllers
![](../images/18_admission_controllers_3.png)

### Enabling NamespaceAutoProvision
After we enable this admission controller, namespace will be created if it doesn't exists:
![](../images/18_admission_controllers_4.png)

>NOTE: in newer k8s NamespaceAutoProvision & NamespaceExists is replaced with NamespaceLifecycle

## Validating & mutating admission controller

Validating - E.g. NamespaceExists - validates if namespace exists and rejects request if it does not.

Mutating - E.g. DefaultStorageClass - so that when request for PVC comes without storage class, request will be mutated and default storage class will be added.

Some admission controllers can be both validating and mutating. In this case mutation should come first.

## External Admission controllers
MutatingAdmissionWebhook and ValidatingAdmissionWebhook
![](../images/18_admission_controllers_5.png)

### Custom webhook server
Can be deployed inside k8s
![](../images/18_admission_controllers_6.png)
![](../images/18_admission_controllers_7.png)
In this case every creation of pod will trigger call to webhook service and validation will be checked with returned json.
