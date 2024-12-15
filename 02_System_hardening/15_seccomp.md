# Seccomp (secure computing)
Can be used to sandbox application to only use syscalls they need

![](../images/15_seccomp_1.png)
![](../images/15_seccomp_2.png)
value 2 means seccomp is enabled in container

![](../images/15_seccomp_3.png)

## Default docker seccomp filter
![](../images/15_seccomp_4.png)

## Whitelisting and blacklisting
Whitelisting blocks all and only enables selected ones.  
Blacklisting allows all and only disables selected ones (less secure).
![](../images/15_seccomp_5.png)

## Blocked syscalls by default
![](../images/15_seccomp_6.png)

## Custom seccomp
Disabling mkdir:
![](../images/15_seccomp_7.png)

## Allow all syscalls
![](../images/15_seccomp_8.png)
Unconfined allows all, but setting date still doesn't work because of other security mechanisms ([Capabilities](17_linux_capabilities.md)).

## Seccomp in kubernetes
Kubernetes unlike docker does not implement seccomp by default (it's set to unconfined):
![](../images/15_seccomp_9.png)
![](../images/15_seccomp_10.png)

To enable seccomp in a pod:
![](../images/15_seccomp_11.png)
![](../images/15_seccomp_12.png)

To enable custom seccomp profile in a pod:
![](../images/15_seccomp_13.png)
![](../images/15_seccomp_14.png)
![](../images/15_seccomp_15.png)
How to read those syscall numbers?
![](../images/15_seccomp_16.png)

Test what happens with profile that blocks everything:
![](../images/15_seccomp_17.png)
![](../images/15_seccomp_18.png)
