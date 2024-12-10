# Kubelet security

Kubelet config was moved to yaml:
![](../images/07_kubelet_1.png)
![](../images/07_kubelet_2.png)
![](../images/07_kubelet_3.png)
other apis:
![](../images/07_kubelet_4.png)
![](../images/07_kubelet_5.png)

## Disable anonymous authentication
It's best practise.
![](../images/07_kubelet_6.png)

## Enable authentication with certificates
![](../images/07_kubelet_7.png)

## Authorization
Change from AlwaysAllow to Webhook - best practise
![](../images/07_kubelet_8.png)
then kubelet talks to apiserver to check if request is allowed.

## Disable read-only port
Set readOnlyPort to 0:
![](../images/07_kubelet_9.png)