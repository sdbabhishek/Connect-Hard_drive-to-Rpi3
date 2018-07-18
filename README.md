# Connect-Hard_drive-to-Rpi3   (Reference  www.makeuseof.com)
Auto detect HDD on reboot of RPI3


More convenient is the option to use the ntfs-3g software, so that the Raspberry Pi can read the
NTFS file system:

sudo apt install ntfs-3g

Note: Swap “mydisk” with your preferred disk label.
Assign permissions with:

sudo chmod 770 /mnt/mydisk

Next, mount the drive with:

sudo mount -t ntfs-3g -o uid=1000,gid=1000,umask=007 /dev/sda1 /mnt/mydisk

Once you’ve done this, you should be able to access the drive in Raspbian. But what if you want to
access the disk after a reboot?
The answer is to edit the fstab. Begin by backup:

sudo cp /etc/fstab /etc/fstab.backup

Next, edit the original:

sudo nano /etc/fstab

Add the information need to mount the disk; this begins with the 16-character UUID string you made
a note of earlier:

UUID=ABCDEFGH12345678 /mnt/volume ntfs-3g uid=1000,gid=1000,nofail,umask=007 0 0

Next, reboot:

sudo reboot

You should now find that the HDD storage is accessible each time you boot up your Raspberry Pi.
