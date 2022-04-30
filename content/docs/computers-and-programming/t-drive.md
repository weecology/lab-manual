---
title: "Accessing the T-drive"
type: book
summary: " "
---

If off campus, turn on the virtual private network (VPN) before connecting using the instructions here: https://vpn.ufl.edu/

## Windows

* Follow the instructions here: https://wec.ifas.ufl.edu/resources/it--computer-support/mapping-your-t-and-u-drives/

## Mac

* Open the Finder, and from the menu bar select **Go > Connect to Server**.
* Enter `smb://ad.ufl.edu/ifas/wec/groups/` as the "server address.
* If you'd like to keep this URL stored as a "favorite", click the `+` next to the address bar
* Click "Connect"
* Lab materials are in the `lab-white-ernest` folder.

## Linux

Assuming you're running Ubuntu. Install the cifs-utils package, create a folder called /media/T for a mount point, then run the mount command, replacing `<your-ufid>` with your ufid (the same one used for email). You will be prompted for your password.

    sudo apt-get install cifs-utils
    sudo mkdir /media/T
    sudo mount -t cifs //ad.ufl.edu/ifas/wec/groups /media/T -o username=<your-ufid>