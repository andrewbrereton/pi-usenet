# Mount to NAS

```
sudo mkdir -p /mnt/movies
sudo mkdir -p /mnt/tv
sudo chmod -R 777 /mnt
echo "//192.168.1.10/movies /mnt/movies cifs username=pi,password=,noserverino,iocharset=utf8,file_mode=0777,dir_mode=0777,rw,nosetuids,uid=102,gid=100,noperm 0 0" | sudo tee -a /etc/fstab
echo "//192.168.1.10/tv /mnt/tv cifs username=pi,password=,iocharset=utf8,noserverino,file_mode=0777,dir_mode=0777,rw,nosetuids,uid=sickbeard,gid=users,noperm 0 0" | sudo tee -a /etc/fstab
sudo mount -a
```
