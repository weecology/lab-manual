Windows:

* Follow the instructions here: http://www.wec.ufl.edu/resources/IT/network_drives.php

Mac: 

* If off campus, turn on the virtual private network (VPN) using the instructions here: https://vpn.ufl.edu/
* Open the Finder, and from the menu bar select **Go > Connect to Server**.
* Enter `cifs://ad.ufl.edu/clas/share` as the "server address.
* If you'd like to keep this URL stored as a "favorite", click the `+` next to the address bar
* Click "Connect"
* Lab materials are in the `lab-white-ernest` folder.

Linux: 

Assuming your running Ubuntu. Install the cifs-utils package, create a folder called /media/T for a mount point, then run the mount command, replacing <your-ufid> with your ufid (the same one used for email). You will be prompted for your password.

    sudo apt-get install cifs-utils
    sudo mkdir /media/T
    sudo mount -t cifs //ad.ufl.edu/ifas/wec/groups /media/T -o username=<your-ufid>
