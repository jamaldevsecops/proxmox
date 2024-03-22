(B) Configure Cluster
=================================================
1. Create a new cluster via server1 (proxmox1.apsis.local)
```
pvecm create ProxmoxCluster
```
2. Join server2 and server3 in the cluster 
```
pvecm add proxmox1.apsis.local (Cluster is created on the server1)
```
```
pvecm status 
```
