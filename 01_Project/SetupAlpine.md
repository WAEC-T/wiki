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
14. If it still does not work, run ip link
15. Check if wlan0 is up
16. Run ip route and check the gateway and the IP
17. If not, enter manually in vi /etc/wpa_supplicant.conf
18. Add
`ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=DK
... and your network credentials to network: {ssid: ... psk: ...}`
    
20. Lastly, run ip link set wlan0 up if it is still down
21. Run wpa_supplicant -B -i wlan0 -c /etc/wpa_supplicant/wpa_supplicant-conf
22. As a bonus, run setup-interface to scan for networks again
23. Also, add udhcpc -i wlan0
24. Try ip route again
25. apk upgrade and apk update
26. what if is fails here ? :(
27. Then you check the step 10 again
28. BAM!
