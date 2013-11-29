# Install CouchPotato

```
sudo su
useradd --system --user-group --no-create-home couchpotato
git clone git://github.com/RuudBurger/CouchPotatoServer.git
mv CouchPotatoServer /usr/local/couchpotato
chown -R couchpotato:couchpotato /usr/local/couchpotato
mkdir /var/couchpotato
chown -R couchpotato:couchpotato /var/couchpotato
cp /usr/local/couchpotato/init/ubuntu /etc/init.d/couchpotato
cat > /etc/default/couchpotato <<EOF
CP_HOME=/usr/local/couchpotato
CP_USER=root
CP_DATA=/var/couchpotato
CP_OPTS=--config_file=/var/couchpotato/couchpotato.ini
EOF
exit
```

## Test

    sudo /etc/init.d/couchpotato start

http://192.168.1.3:5050

ctrl c
