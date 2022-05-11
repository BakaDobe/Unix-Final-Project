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
- An easy way to create public and private SSH keys is with PuTTYgen
- First things first, make sure that the type of key to be generated is on "RSA" and that the number of bits is "4096"
- Press "Generate" and the key will do so
- Copy the public key in the display box and save it in Notepad to use later
- To make the key secure, add a passphrase(password) and once you're done, save it as a private key and give it a name
- You can now close the key generator

## Accessing Remote Server
-

## Update & Upgrade
-

## Creating users
-

## Changing root password
-

## Adding keys to dedicated location
-

## Nginx and Nmap installation
-

## WinSCP installation
-

## Authentication of remote web server
-
