# Shared disks


This is to mount the shared disks. Only mount those that you need.

You can found the disk paths at the following webpage. 
[https://www.internal.eawag.ch/fileadmin_intranet/intranet/informatik/admin/fileservices/fileservices_shares_anb.pdf](https://www.internal.eawag.ch/fileadmin_intranet/intranet/informatik/admin/fileservices/fileservices_shares_anb.pdf)

I noticed that the aquascope path is missing from the document, `//eaw-data/AquaScope_data$`.

Note that you need to either be physically at Eawag, or your VPN should be active when you try to access these disks.

### Mounting automatically on Ubuntu


1) Create the directories where you want to install the disks, and install `keyutils` and cifs-utils.
```
sudo apt-get install keyutils cifs-utils
mkdir /mnt/Siam /mnt/scratch-disk
```

2) Get user id (uid) and group id (gid) with: 
```
username=`whoami`
sudo id $username
```

3) Add the following to "/etc/fstab" (one line for each disk). Replace the values of uid and gid with your user id:
```
//eaw-depts/siam$ /mnt/Siam cifs uid=1000,gid=1000,credentials=/home ~/.smbcredentials,iocharset=utf8
//eaw-various/Scratch-disk$ /mnt/scratch-disk cifs uid=1000,gid=1000,credentials=~/.smbcredentials,iocharset=utf8
```

4) Create the file `~/.smbcredentials` with the following content:
```
username=YOUR_EAWAG_USERNAME #Not the linux username
password=YOUR_EAWAG_PASSWORD # Yes, it's a huge security flaw
domain=Eawag
```

5) Reload `fstab` with:
```
sudo mount -a
```

The process works and it is very convenient. However, as you noticed, there is a relevant security flaw. If you find better solutions please tell me.




### More resources

Auto mount samba share
see [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently).

2) get user id with: sudo id **linux user name**
2) add to "/etc/fstab" (in one line) and replace uid=XXX with your user id:

                  //eaw-depts/siam$ /mnt/Siam cifs uid=1000,gid=1000,credentials=/home/scheidan/.smbcredentials,iocharset=utf8
//eaw-various/Scratch-disk$ /mnt/scratch-disk cifs uid=1000,gid=1000,credentials=/home/scheidan/.smbcredentials,iocharset=utf8

3) create the file "/home/scheidan/.smbcredentials" with:
username=scheidan
password=**eawagPW**
domain=Eawag

4) reload fstab with:
sudo mount -a


