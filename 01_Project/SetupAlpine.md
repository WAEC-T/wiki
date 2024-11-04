# Setup Alpine of Raspberry Pi's

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
11. Add a line with your mirror: https://dl-cdn.alpinelinux.org/alpine/latest-stable/main
12. Run apk-update and Run apk-upgrade
13. Try curl something and see if it works
