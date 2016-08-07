This guide allows you to enable transmission on a WD MyCloud with firmware version 2.

The WD MyCloud with v2 firmwares already contain a transmission binary in the official
firmware. However, no supporting files are provided, making it almost impossible to 
use the BitTorrent client. This repository contains the necessary files to automatically
start transmission and use the web frontend.

This guide is only tested with firmware 2.21.111

Installation
============
Make sure you have activated ssh access in the mycloud web frontend (http://mycloud.local).
To be able to login on a recent ssh client you must add the following lines to your 
`~/.ssh/config`:

    Host wdmycloud.local
        User sshd
        HostkeyAlgorithms +ssh-dss

On your host computer on the same network run the following commands. 

* Install a init script that starts transmission on boot

    `scp transmission-daemon sshd@wdmycloud.local:/etc/init.d/`

* Install the missing files for the web frontend

    `scp -r web sshd@wdmycloud.local:/usr/share/transmission/`

* Disable the RPC whitelist. This allows any user on your network to access the web frontend.

    `ssh sshd@wdmycloud.local`
    `sed -i "/rpc-whitelist-enabled/c\"rpc-whitelist-enabled\": false," .config/transmission-daemon/settings.json`
 
* You may want to edit other settings of transmission

    `ssh sshd@wdmycloud.local`
    `vi .config/transmission-daemon/settings.json`

* Restart your mycloud and access the transmission frontend 
    
    `http://wdmycloud.local:9091`

