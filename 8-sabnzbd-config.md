# SABnzbd Config

http://192.168.1.3:8080/wizard/
language: english
host: ssl.astraweb.com
port: 563
username: ******************
password: ******************
connections: 50
ssl: true
password protect: true
username: ******************
password: ******************
https: true
newzbin.se username: ******************
newzbin.se password: ******************
restart and go to config
General/Host = 0.0.0.0
Folders/Temporary Download Folder = /var/multimedia/incoming/sabnzbd/incomplete
Folders/Completed Download Folder = /var/multimedia/incoming/sabnzbd/complete
Post-Processing Scripts Folder = /usr/local/sickbeard/autoProcessTV
Categories = add three as follows:
movies, default, default, default, /mnt/movies
tv, default, default, sabToSickBeard.py, /mnt/tv
