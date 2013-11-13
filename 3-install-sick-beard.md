# Install Sick Beard

    sudo useradd --system --user-group --no-create-home sickbeard
    git clone git://github.com/midgetspy/Sick-Beard.git
    sudo mv Sick-Beard /usr/local/sickbeard
    sudo chown -R sickbeard:nzb /usr/local/sickbeard
    sudo chmod ug+rw /usr/local/sickbeard/autoProcessTV/
    sudo mkdir /var/sickbeard
    sudo chown sickbeard:nzb /var/sickbeard

## Test

    sudo su sickbeard -c "/usr/local/sickbeard/SickBeard.py --datadir /var/sickbeard --config /var/sickbeard/sickbeard.ini"

https://192.168.1.3:8081

ctrl c
