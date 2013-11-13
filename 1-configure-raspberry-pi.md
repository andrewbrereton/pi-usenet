# Configure Raspberry Pi

Install Raspian

    ssh pi@HOSTNAME

Password: raspberry

    sudo apt-get update
    sudo apt-get upgrade
    sudo raspi-config

expand file system
change password
internationalisation

    sudo apt-get -y purge gnome-icon-theme gnome-themes-standard lxappearance \
    lxde-common lxinput lxpanel lxpolkit lxrandr lxsession-edit lxshortcut lxtask \
    lxterminal scratch xserver-common

    sudo apt-get -y autoremove
    sudo apt-get -y autoclean

Update Pi

    git clone git://github.com/Hexxeh/rpi-update.git
    cd rpi-update
    sudo ./rpi-update
    raspi-config
    
set memory split to 240 MB RAM and 16 MB video

    /boot/config.txt gpu_mem 16

expand_rootfs

    sudo reboot

    sudo apt-get -y install python2.6 python-cheetah python-openssl par2

    sudo sh -c "echo \"deb-src http://mirrordirector.raspbian.org/raspbian/ wheezy main contrib non-free rpi\" >> /etc/apt/sources.list"
    sudo apt-get update
    sudo apt-get -y build-dep unrar-nonfree
    sudo apt-get source -b unrar-nonfree
    sudo dpkg -i unrar*.deb

    sudo addgroup nzb
