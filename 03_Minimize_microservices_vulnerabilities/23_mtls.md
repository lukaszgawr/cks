# mTLS - mutual TLS

Mutual verification of TLS certificate (client & server).
For mTLS pod-to-pod communication can be used tools such as Istio and Linkerd (Service Mesh).

![](../images/23_mtls_1.png)

Different modes supported by Istio:

![](../images/23_mtls_2.png)
![](../images/23_mtls_3.png)
drawback - not all external applications support mTLS.