# Audit logs
Auditing is disabled by default.

## Requests in k8s
Request - e.g. create nginx pod
![](../images/34_audit_logs_1.png)
Request is made to kube-apiserver. Then sequence is as follows
1. RequestReceived - event generated in respect to validity of the request, authentication and authorization
2. ResponseStarted - event generated that need some time to complete. E.g. if you add --watch flag
3. ResponseComplete
4. Panic - in case of errors

## Audit policy
![](../images/34_audit_logs_2.png)
Levels (lowest to hightest verbosity):
* None
* Metadata - only timestamp, resources, words will be logged
* Request
* RequestResponse

## Enabling auditing in the cluster
![](../images/34_audit_logs_3.png)
Effect:
![](../images/34_audit_logs_4.png)



