(A) Prepare OS (For All Proxmox VE)
=================================================
1. Update locales if your setup is not en_US-UTF8 (on all servers).
```
dpkg-reconfigure locales
```	
(Pres Enter)

2. Update /etc/hosts (on all servers). 
```
nano /etc/hosts
```
```
192.168.10.101 proxmox1.apsis.local
192.168.10.102 proxmox2.apsis.local
192.168.10.103 proxmox3.apsis.local
```


3. Enable No-Subscription (on all servers). 

Proxmox VE No-Subscription Repository:  
Source: https://pve.proxmox.com/wiki/Package_Repositories
```
mv /etc/apt/sources.list /etc/apt/sources.list.default
nano /etc/apt/sources.list
```
Past the following contents. 
```
deb http://ftp.debian.org/debian bookworm main contrib
deb http://ftp.debian.org/debian bookworm-updates main contrib

# Proxmox VE pve-no-subscription repository provided by proxmox.com,
# NOT recommended for production use
deb http://download.proxmox.com/debian/pve bookworm pve-no-subscription

# security updates
deb http://security.debian.org/debian-security bookworm-security main contrib
```
```
rm /etc/apt/sources.list.d/pve-enterprise.list
```

4. Update (on all servers).
```
apt-get update
apt-get upgrade
```

(B) Configure Cluster
=================================================
1. Create a new cluster via server1 (proxmox1.apsis.local)
```
pvecm create ApsisCluster
```
2. Join server2 in the cluster 
```
pvecm add proxmox1.apsis.local (Cluster is created on the server1)
```
```
pvecm status 
```

