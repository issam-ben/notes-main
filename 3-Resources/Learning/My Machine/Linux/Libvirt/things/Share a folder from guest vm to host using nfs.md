
1- install nfs according to your distro.
2- enable and start nfs service using systemctl.
3-allow nfs service through firewall:
```
sudo firewall-cmd --permanent --add-service=nfs
sudo firewall-cmd --permanent --add-service=mountd
sudo firewall-cmd --permanent --add-service=rpc-bind
sudo firewall-cmd --reload
```
4-create a folder on host system where you will mount
```
mkdir /path/to/shared/folder/
```
5- mount folder in Host:
```
sudo mount <guest_ip>:/path/to/shared/folder /mnt/shared_folder
```
