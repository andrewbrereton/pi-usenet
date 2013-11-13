# Install SABnzbd

    sudo useradd --system --user-group --no-create-home --groups nzb sabnzbd
    wget http://downloads.sourceforge.net/project/sabnzbdplus/sabnzbdplus/0.7.16/SABnzbd-0.7.16-src.tar.gz
    tar xzf SABnzbd-0.7.16-src.tar.gz
    sudo mv SABnzbd-0.7.16 /usr/local/sabnzbd
    sudo chown -R sabnzbd:nzb /usr/local/sabnzbd
    sudo mkdir /var/sabnzbd
    sudo chown sabnzbd:nzb /var/sabnzbd

## Test

    sudo su sabnzbd -c "/usr/local/sabnzbd/SABnzbd.py -f /var/sabnzbd -s 192.168.1.3:8080"

http://192.168.1.3:8080

ctrl c
