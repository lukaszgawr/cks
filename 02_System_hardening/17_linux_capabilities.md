# Linux capabilities

Before kernel 2.2 privileged process could do anything. But starting from version 2.2 privileged process permissions were divided into capabilites:
![](../images/17_capabilities_1.png)

## Checking which capabilites are required for processes
![](../images/17_capabilities_2.png)


## Default capabilities in a linux kernel:
By default date cannot be changed because this capability is not enabled in kernel by default. So even if seccomp is set to unconfined, setting date will be denied:
![](../images/17_capabilities_3.png)

## Adding capabilities to pods
![](../images/17_capabilities_4.png)

## Dropping capabilities
![](../images/17_capabilities_5.png)


