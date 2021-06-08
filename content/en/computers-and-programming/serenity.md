## Overview
Some useful commands to help navigate and use Serenity

To log into Serenity, you will need to be under the university network or use a [VPN](https://it.ufl.edu/ict/documentation/network-infrastructure/vpn/) provided by the university.

Login in

ssh username@serenity.ifas.ufl.edu

In case of the warnings below

```
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
```
edit `~/.ssh/known_hosts` and remove the line with serenity

To change your password, use 

`passwd username`

OR

`sudo passwd username`

[To set up ssh keys](https://github.com/weecology/lab-wiki/wiki/Programming:-SSH-&-SSH-keys-for-GitHub---Serenity---etc) 
 
[RStudio on serenity](https://github.com/weecology/lab-wiki/wiki/Programming:-RStudio-on-serenity)