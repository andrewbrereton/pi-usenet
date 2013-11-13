# Init Scripts

```
sudo tee /etc/init.d/sabnzbd<<"EOF"
#!/bin/sh
### BEGIN INIT INFO
# Provides:          SABnzbd
# Required-Start:    $network $remote_fs $syslog
# Required-Stop:     $network $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start SABnzd at boot time
# Description:       Start SABnzbd.
### END INIT INFO

case "$1" in
start)
  echo "Starting SABnzbd."
  /usr/bin/sudo -u sabnzbd -H /usr/local/sabnzbd/SABnzbd.py -d -f /var/sabnzbd/sabnzbd.ini
;;
stop)
  echo "Shutting down SABnzbd."
  p=`ps aux | grep -v grep | grep SABnzbd.py | tr -s \ | cut -d ' ' -f 2`
  if [ -n "$p" ]; then
    kill -2 $p > /dev/null
    while ps -p $p > /dev/null; do sleep 1; done
  fi
;;
*)
  echo "Usage: $0 {start|stop}"
  exit 1
esac
exit 0
EOF
```

```
sudo tee /etc/init.d/sickbeard<<"EOF"
#!/bin/sh
### BEGIN INIT INFO
# Provides:          SickBeard
# Required-Start:    $network $remote_fs $syslog
# Required-Stop:     $network $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start SickBeard at boot time
# Description:       Start SickBeard.
### END INIT INFO

case "$1" in
start)
  echo "Starting SickBeard."
  /usr/bin/sudo -u sickbeard -H /usr/local/sickbeard/SickBeard.py -d --datadir /var/sickbeard --config /var/sickbeard/sickbeard.ini
;;
stop)
  echo "Shutting down SickBeard."
  p=`ps aux | grep -v grep | grep SickBeard.py | tr -s \ | cut -d ' ' -f 2`
  if [ -n "$p" ]; then
    sb_api_key=`grep -m 1 api_key ${sb_config} | cut -d ' ' -f 3`;
    sb_port=`grep -m 1 web_port ${sb_config} | cut -d ' ' -f 3`;
    wget -q --delete-after http://localhost:${sb_port}/api/${sb_api_key}/\?cmd=sb.shutdown
    while ps -p $p > /dev/null; do sleep 1; done
  fi
;;
*)
  echo "Usage: $0 {start|stop}"
  exit 1
esac

exit 0
EOF
```

```
sudo tee /etc/init.d/couchpotato<<"EOF"
#!/bin/sh
### BEGIN INIT INFO
# Provides: CouchPotato
# Required-Start: $network $remote_fs $syslog
# Required-Stop: $network $remote_fs $syslog
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# Short-Description: Start CouchPotato at boot time
# Description: Start CouchPotato.
### END INIT INFO
case "$1" in
start)
 echo "Starting CouchPotato."
 /usr/bin/sudo -u couchpotato -H /usr/local/couchpotato/CouchPotato.py --daemon --data_dir=/var/couchpotato --config_file=/var/couchpotato/couchpotato.ini
;;
stop)
 echo "Shutting down CouchPotato."
  p=`ps aux | grep -v grep | grep CouchPotato.py | tr -s \ | cut -d ' ' -f 2`
  couch_api_key=`grep -m 1 api_key /var/couchpotato/couchpotato.ini | cut -d ' ' -f 3`;
  couch_port=`grep -m 1 port /var/couchpotato/couchpotato.ini | cut -d ' ' -f 3`;
 wget -q --delete-after http://localhost:${couch_port}/api/${couch_api_key}/app.shutdown
 while ps -p $p > /dev/null; do sleep 1; done
;;
*)
 echo "Usage: $0 {start|stop}"
 exit 1
esac
exit 0
EOF
```

```
sudo chmod 755 /etc/init.d/sabnzbd /etc/init.d/sickbeard /etc/init.d/couchpotato
sudo update-rc.d sabnzbd defaults
sudo update-rc.d sickbeard defaults
sudo update-rc.d couchpotato defaults
```

```
sudo /etc/init.d/sabnzbd start
sudo /etc/init.d/sickbeard start
sudo /etc/init.d/couchpotato start
```
