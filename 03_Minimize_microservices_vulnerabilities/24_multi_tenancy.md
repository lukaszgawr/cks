# Multi-tenancy

![](../images/24_multi_tenancy_1.png)
![](../images/24_multi_tenancy_2.png)
![](../images/24_multi_tenancy_3.png)

## API Priority & Fairness

![](../images/24_multi_tenancy_4.png)
![](../images/24_multi_tenancy_5.png)
Those priorities were set on namespace, but can be set on any of these:
![](../images/24_multi_tenancy_6.png)
## Pod priority and preemption
![](../images/24_multi_tenancy_7.png)
![](../images/24_multi_tenancy_8.png)

## Comparison of both
![](../images/24_multi_tenancy_9.png)

## QoS
Resource requests and limits in terms of resources.
In terms of network:
![](../images/24_multi_tenancy_10.png)
it's a calico network policy  

In terms of storage:
![](../images/24_multi_tenancy_11.png)

## DNS isolation

![](../images/24_multi_tenancy_12.png)
this coredns config makes name resolution possible only within pods own namespace.

