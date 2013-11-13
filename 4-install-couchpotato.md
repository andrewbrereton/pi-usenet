# Install CouchPotato

    sudo useradd --system --user-group --no-create-home couchpotato
    git clone git://github.com/RuudBurger/CouchPotatoServer.git
    sudo mv CouchPotatoServer /usr/local/couchpotato
    sudo chown -R couchpotato:couchpotato /usr/local/couchpotato
    sudo mkdir /var/couchpotato
    sudo chown -R couchpotato:couchpotato /var/couchpotato

## Test

    sudo su couchpotato -c "/usr/local/couchpotato/CouchPotato.py --data_dir=/var/couchpotato --config_file=/var/couchpotato/couchpotato.ini"

http://192.168.1.3:5050

ctrl c
