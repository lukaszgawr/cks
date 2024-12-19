# Immutable containers
By default you can copy config to containers and have config drift. To ensure immutability of containers you must change root filesystem to read only (but remember about writeable /var/ for some catalogs):

![](../images/33_immutable_containers_1.png)

Effect:
![](../images/33_immutable_containers_2.png)

Refrain from using privileged containers. This is what can happen despite having read only file system:
![](../images/33_immutable_containers_3.png)

Best practise: add PSP:
![](../images/33_immutable_containers_4.png)

