# Recreation

- [VPS installation](#vps-installation)
- [Putty installation](#putty-installation)
- [SSH Keys](#ssh-keys)
- [Accessing Remote Server](#accessing-remote-server)
- [Update & Upgrade](#update--upgrade)
- [Creating users](#creating-users)
- [Changing root password](#changing-root-password)
- [Adding keys to dedicated location](#adding-keys-to-dedicated-location)
- [Nginx and Nmap installation](#nginx-and-nmap-installation)
- [WinSCP installation](#winscp-installation)
- [Authentication of remote web server](#authentication-of-remote-web-server)

## VPS installation
- Go to [ionos.ca](https://ionos.ca/servers/vps) and select the $1/month plan
- This is the cheapest and best option for our project with 512MB RAM, 10GB SSD and a 1vCore CPU
- For "System and version management system", pick Debian 11
- Make sure the "Data center location" is on United States and you select any Cloud Backup
- Before you can checkout, create your account and provide your personal information (email, phone number, address, etc..)
- After the purchase, log into your newly created account and go to "Servers & Cloud"
- Here you will find the server's IP address, the default username and password(you can change this once in the server), the server's status and which port they can connect to

## Putty installation
- Go to [putty.org](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) to download both PuTTy (a SSH and telnet client) and PuTTYgen (creates SSH keys)
- We chose the 64-bit x86 option because our machines met those requirement

## SSH Keys
- An easy way to create a public and private SSH key is with PuTTYgen
	- First things first, make sure that the type of key to be generated is on "RSA" and that the number of bits is "4096"
	- Press "Generate" and the key will do so
	- Copy the public key in the display box and save it in Notepad to use later
	- To make the key secure, add a passphrase(password) and once you're done, save it as a private key and give it a name
- You can now close the key generator

## Accessing Remote Server
- To access the remote server, you'll need to open PuTTY
	- Paste the server's IP address where it says "Host Name (or IP address)"
	- Make sure the port is on 22 and that the connection type is on "SSH with Telnet selected"
	- Press Open and follow what the popup says
	- Enter the username (the one provided by ionos) when asked, then press enter
	- Enter the default password (the one provided by ionos) when asked (it's normal for the screen to remain the same even though you're typing), press enter when you're done

## Update & Upgrade
- Before anything, you'll need to update and update the system
	- You need to run: `~# sudo apt-get update` and `~# sudo apt-get upgrade` 
	- Enter 'Y' to continue

## Creating users
- To create a user, you need to run: `~# sudo useradd username` (where username can be changed to whatever name you desire)
- To add a user to sudoers, run: `~# usermod -aG sudo username` (again where username can be changed to what you want)
- To verify that the user is part of the sudo group, enter: `~# groups username` 
- To log into another user, run: `~# su username`

## Changing root password
- If you want a simpler and shorter password for your root, run: `~# sudo passwd root`
	- Not only are you personalizing it, but you're making it secure

## Adding keys to dedicated location
- Now, to add the SSH keys to the system:
	- Copy the public key that was saved in the Notepad
	- In the system, run: `~# nano ~/.ssh/authorized_keys`
	- Right click the mouse to paste the key
	- Hit `Ctrl + o` to save the key, press enter to confirm and hit `Ctrl + x` to exit

## Nginx and Nmap installation
- To install Nginx (HTTP web server), run: `~# sudo apt install nginx`
	- To make sure the service is running, enter: `~# sudo systemctl status nginx.service`
		- If it's not running, enter: `~# sudo systemctl start nginx.service`, the re-enter the code above the verify the status
	- To see and or modify(which we didn't do) the port number of Nginx, run: `~# nano /etc/nginx/sites-enabled/default`
		- ``
		server {
			listen 80 default_server;
			listen [::]:80 default_server;
		}
		``
		- `80` is the port number that can be changed (we kept it at 80)
- To install Nmap (network scanner), run `~# sudo apt install nmap`
	- To check all TCP port on your system, enter: `~# sudo nmpa -sT IPAddress` (in IPAddress we 74.208.150.121)
	- ``
	PORT    STATE   SERVICE
	22/tcp  open    ssh
	80/tcp  open    http
	``
	- Both of these ports should be open, 22 for the remote system and 80 for Nginx

## WinSCP installation
- Go to [WinSCP.com](https://winscp.net/eng/download.php) (File exchange between local computer and remote server) and download it.
	- Once the app is open, make sure the file protocol is on "SCP" and the port number is "22", enter the IP address, the username and the password.
	- Once the connection is established, navigate through "var", then "www", then "html"
	- Once there, upload the folder containing the html files into the remote service directory and voila

## Authentication of remote web server
- Go into whatever web browser you have (Chrome, firefox, Edge)
	- Add the IP address into the search bar and add the folder/file you wan to open
		- Example: `74.208.150.121/Anthony/home.html`
		- The html page should be on display
