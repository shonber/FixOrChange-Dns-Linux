# FixOrChange-Dns-Linux
How to change or fix DNS issues on Linux OS.


1) sudo nano /etc/dhcp/dhclient.conf // Change #prepend domain-name-servers line, add the dns you want. Example:
prepend domain-name-servers 1.1.1.1, 1.0.0.1; // Remove # so that it isnt a comment

2) sudo chattr -i /etc/resolv.conf/

3) sudo nano /etc/resolv.conf/ // Change your DNS settings. IMPORTANT NOTE: Dont separate DNS adresses with commas, write nameserver before each adress, like here:
nameserver 1.1.1.1
nameserver 1.0.0.1
nameserver 8.8.8.8
nameserver 8.8.4.4

4) sudo chattr +i /etc/resolv.conf/

5) sudo systemctl restart NetworkManager.service // If it doesnt work use sudo service restart NetworkManager. It isnt that necessary, wont change outcome.


Explaination:

You modifided /etc/dhcp/dhclient.conf and added the adresses, Then used chattr -i to set /etc/resolv.conf/ as a writable file, then changed the file again, set /etc/resolv.conf/ as unwritable and restarted Network Manager*/
