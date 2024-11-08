# Setup Alpine of Raspberry Pi's

---
### Partioning:
* Run:
* `diskutil unmountDisk /dev/disk2` unmount 
* `diskutil partitionDisk /dev/disk2 MBRFormat FAT32 RPI_BOOT 50% FAT32 SETUP 50%` do the partioning
* copy files from: https://alpinelinux.org/downloads/ - armhf
* 





1. Download the armhf Alpine.tar.gz
2. Partition SD-card to have a bootable Alpine-partition
3. Plug everything in the Raspberry Pi including WIFI-dongles BEFORE booting.

---------------- NETWORK SETUP ------------------

4. During setup alpine, choose default for eth0 
5. It will most likely fail to connect
5. Then, for your WIFI-dongle (wlan0) scan for networks
6. Select your network
7. Give credentials
8. Make sure it return an IP-address
9. Continue setup-alpine until the end
10. Configure the mirror for alpine by executing: vi /etc/apk/repositories
11. Add a line with your mirror: 
    * https://eu.edge.kernel.org/alpine/edge/main
    * https://eu.edge.kernel.org/alpine/edge/community
12. Run apk-update and Run apk-upgrade
13. Try curl something and see if it works
14. If it still does not work, run ip link
15. Check if wlan0 is up
16. Run ip route and check the gateway and the IP
17. If not, enter manually in vi /etc/wpa_supplicant.conf
18. Add
`ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=DK
... and your network credentials to network: {ssid: ... psk: ...}`
    
1.  Lastly, run ip link set wlan0 up if it is still down
2.  Run wpa_supplicant -B -i wlan0 -c /etc/wpa_supplicant/wpa_supplicant-conf
3.  As a bonus, run setup-interface to scan for networks again
4.  Also, add udhcpc -i wlan0
5.  Try ip route again
6.  apk upgrade and apk update
7.  what if is fails here ? :(
8.  Then you check the step 10 again
9.  BAM!


* Command finding the quickest mirror:
`setup-apkrepos -cf`


----

Step 1: Boot the Raspberry Pi
Insert the SD card into the Raspberry Pi.
Boot into Alpine Linux using the RPI_BOOT partition, which contains the alpine-rpi boot files.
Step 2: Set Up the Second Partition as Persistent Storage
Since everything is being loaded into RAM currently (diskless mode), we need to ensure that the second partition (disk2s2) can act as persistent storage.

Step 2.1: Convert the Second Partition from FAT32 to ext4

The second partition is currently formatted as FAT32, which is not suitable for Linux persistence. Let’s convert it to ext4.

Identify the Second Partition:
After booting, use fdisk to list the partitions and confirm the device names:
fdisk -l
The second partition should be something like /dev/mmcblk0p2.
Format the Partition as ext4:
Convert the second partition from FAT32 to ext4 using the following command:
mkfs.ext4 /dev/mmcblk0p2
This command will erase the FAT32 format and reformat it as ext4, which is better suited for Linux storage.
Step 2.2: Make the Second Partition Available for Persistence

Now that the second partition is formatted as ext4, we need to mount it properly and make it persistent.

Create a Mount Point:
Create a directory to use as a mount point for the second partition:
mkdir /media/persist
Mount the Second Partition:
Mount the newly formatted partition (/dev/mmcblk0p2) to the mount point you created:
mount /dev/mmcblk0p2 /media/persist
Make Changes Permanent by Updating /etc/fstab:
We need to make sure that this partition is automatically mounted during the next boot. Edit the /etc/fstab file to include the second partition:
nano /etc/fstab
Add the following line to /etc/fstab:
/dev/mmcblk0p2 /media/persist ext4 rw,relatime,errors=remount-ro 0 1
This line tells the system to mount /dev/mmcblk0p2 at /media/persist with read/write permissions, using the ext4 filesystem.
Verify Mounting:
Use mount -a to mount all filesystems specified in /etc/fstab:
mount -a
If there are no errors, the partition is mounted correctly. You can also check by listing the contents of the mount point:
df -h
This will show if /media/persist is mounted successfully and has the expected available space.
Step 3: Set Up Diskless Mode with Persistent Storage
Now that we have the second partition (/media/persist) set up, we need to configure Alpine Linux to use it as persistent storage.

Remount the Boot Partition as Read/Write:
First, make sure that the boot partition (RPI_BOOT) is mounted as read/write so we can make necessary changes:
mount /media/mmcblk0p1 -o rw,remount
Create the Loopback Image on the Second Partition:
To create a loopback image for persistent storage:
dd if=/dev/zero of=/media/persist/persist.img bs=1024 count=0 seek=1048576
This command creates an empty file named persist.img of size 1 GB (you can adjust the size if you want more persistent storage).
Format the Loopback Image:
Format the newly created loopback image as ext4:
mkfs.ext4 /media/persist/persist.img
Mount the Loopback Image:
Add the loopback image to /etc/fstab to ensure it is mounted during boot:
echo "/media/persist/persist.img /media/overlay ext4 loop,rw,relatime,errors=remount-ro 0 0" >> /etc/fstab
Create a mount point for the overlay:
mkdir /media/overlay
Mount all filesystems:
mount -a
Verify the Setup:
Check if the loopback image is mounted at /media/overlay:
df -h
Ensure /media/overlay shows up in the list of mounted filesystems, indicating that the persistent storage is ready.
Step 4: Configure Alpine for Diskless Mode Persistence
Now that the persistent storage is ready, you can configure Alpine Linux to store changes persistently.

Save Configurations:
Use the Alpine utility to save the current system configuration to the persistent storage:
lbu add /media/overlay
lbu commit -d /media/overlay
Reboot and Test:
Reboot the Raspberry Pi:
reboot
After the reboot, check if the configurations and any test files you created are still present. This will confirm that the persistence is working as expected.
Summary
Partition Setup: The SD card has two partitions (RPI_BOOT as FAT32 for boot files and /dev/mmcblk0p2 converted to ext4 for persistence).
Loopback Image: A loopback image (persist.img) is created in the second partition for persistent storage.
Mounting and Persistence: The loopback image is mounted at /media/overlay, and changes are configured to be saved persistently.





* After make sure that the mirrors are set 
* run `apk update`
* run `apk upgrade`
  
Installed docker
* run `apk add docker`
* 


