# Open Policy Agent (OPA)

Not taking k8s into consideration yet we need to run a server:
![](../images/21_opa_1.png)
After OPA service is running we need to load policy:
![](../images/21_opa_2.png)
and apps can now use it:
![](../images/21_opa_3.png)

## Policy testing
![](../images/21_opa_4.png)

## OPA in Kubernetes - OPA Gatekeeper
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
