# hello-world
GitHub Guide project

Steps to set up my workstation. (In case I forget them.)

1.	Download the net-install package. 
https://download.fedoraproject.org/pub/fedora/linux/releases/29/Workstation/x86_64/iso/Fedora-Workstation-netinst-x86_64-29-1.2.iso
2.	Create a bootable USB with this image. --I used the Fedora Media Writer tool and selected a custom ISO.
3.	Boot to the USB drive.
4.	Choose your preferred language and click Continue.
5.	Select the network and host name. --Do not attach to a domain at this time.
6.	Set the time zone.
7.	Select the installation source. 
8.	Choose the installation destination. --If you choose a location that is not empty, you will get the opportunity to reclaim the space.
9.	Choose Software Selection. --I chose minimal install on the left and Standard + Domain Membership on the right.
10.	Begin Installation.
11.	Set the root password --Set the password to something complicated but easy to type.
12.	Create a local admin user that is not root. --I chose localhelp and provided an easier password than root.
13.	Install x11
```dnf install @base-x```
14.	Install Xrdp
```dnf install xrdp```
15.	Start Xrdp
```
systemctl start xrdp
systemctl start xrdp-sesman
```
16.	Verify Xrdp is running
```netstat -antup | grep xrdp```
17.	Enable Xrdp after reboot
```
systemctl enable xrdp
systemctl enable xrdp-sesman
```
18.	Set pinhole in firewall
```
firewall-cmd –permanent –add-port=3389/tcp
firewall-cmd --reload
```
19.	Install Cinnamon desktop
```dnf group install cinnamon-desktop ```
20.	Set automatic boot to Cinnamon desktop
```systemctl set-default graphical.target```
21.	Set Cinnamon to Xrdp desktop
```
# echo "cinnamon" > ~/.Xclients
chmod +x ~/.Xclients
# systemctl restart xrdp.service
```
