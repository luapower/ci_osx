LUAPOWER OSX CI SERVER SETUP HOWTO:
----------------------------------------------------------------------

* set Keyboard: fastest setting; invert Option/Command keys.
* set Mouse: disable arrogantly-so-called "natural" scrolling.
* set Terminal:
  * Profile: Pro, Background Opacity: 100.
  * Shell Tab: When the shell exits: close if the shell exited cleanly.

* enable the root user and set a password for it with:
    Directory Utility > Unlock
        App Menu > Edit > Enable Root User
        App Menu > Edit > Set Root Password

* set NOPASSWD:ALL in /etc/sudoers to entries root and %admin.

* set blank passwords for cosmin and root with:
    dscl . -passwd /Users/<user>

* set Automatic login to user Cosmin in:
    System Preferences > Users & Groups > Unlock > Login Options

* `sudo su` to check that we can sudo without a password.

* logout & log back in to check that no password is asked.

* add this machine's MAC to the router's static DHCP table.
  - this fixes the machine's IP which enables using ssh in scripts.

* enable ssh server with:
    Sharing > [x] Remote Login

* add luapower's .ssh/id_rsa and .ssh/authorized_keys from vault, then:
    chmod 700 ~/.ssh
    chmod 600 ~/.ssh/authorized_keys
    chmod 600 ~/.ssh/id_rsa
  
  - allows ssh into the machine with a single key and no password.
  - allows pushing to github with a single key and no password.

* login via ssh to cosmin with the private key.
  - after this, we won't see a password prompt ever again.

* enable VNC server with:
     Sharing > [x] Remote Management > Computer Settings >
        > VNC viewers may control the screen with password"
  - this allows using RealVNC on the machine with a password.

* ./setup-automount : set up an automount for the samba share on the
  Windows machine to /mnt/auto/luapower also symlinked to $HOME/luapower.

* install Git

* install macports

* port install mc

* ./install-mgit



OSX INSTALL HOWTO:
----------------------------------------------------------------------
* find an OSX/MacOS dmg file to restore on the net or a bootable ISO.
* using Disk Utility:
  * make a new 40G partition (type "HPFS+ Journaled" for OSX <= 10.12).
  * use the "Restore" function to restore the dmg to it.
  * boot to that partition by holding the Option key on startup.
  * set up the OS any way you need before backing it up.
  * shrink the partition to 30G using Disk Utility.
  * backup the partition on an external drive by right-clicking
  on the partition and selecting "Make image from <partition>".
  this will create a restorable dmg file that can be restored
  on any partition > 30G.
  * enlarge the partition back to 40G or more use the `diskutil`
  cmdline utility for this as the GUI is buggy and will enlarge
  the Recovery HD partition instead of the system one.



OSX RESTORE HOWTO:
----------------------------------------------------------------------
* using Disk Utility, make a 40G+ partition and restore the backup dmg
to it and boot to it holding the Option key.
