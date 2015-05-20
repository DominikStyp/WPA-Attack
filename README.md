# WPA Attack

# What is this ?
Extremly simple script that can be used to **crack WPA network password**.<br />

# How to use ?
All you have to do is type following command:
```
./WPA-Attack -b [BSSID] -c [CHANNEL] -w [WORDLIST_FILE]
```
**Options explanation:**
- [BSSID] is MAC address of the target
- [CHANNEL] is the network channel
- [WORDLIST_FILE] is a file containing dictionary that you want to use cracking the password

**Optional parameters:**
- -s [SPOOFED_MAC] is the MAC Address that will be used, instead of the original WiFi card's MAC
- -h is used to only **grab handshake** and do not try to crack password using **aircrack-ng**,<br /> 
  so you can crack it later if you wish to, and also **captured handshake** will be stored in **./airodump_logs** directory 

# Examples
Without spoofed MAC (**original MAC** of your card is used): <br />
```
./WPA-Attack -b AA:BB:CC:DD:EE:FF -c 11 -w ./myWordlistFile.txt
```

# How it works
It runs 3 separated **konsole** processes: <br />
- **aircrack-ng** which is used to **crack passphrase using .cap files**
- **airodump-ng** which is used to capture packets from Access Point along with **
- **aireplay-ng** (option -0) which is used to **disconnect connected clients**, so you can capture **WPA Handshake** when client tries to reconnect<br />
To be able to crack **WPA/WPA2 passphrase** you'll need to capture **<a href="http://en.wikipedia.org/wiki/IEEE_802.11i-2004" target="_blank">Four-Way Handshake</a>** first.<br />
This information should pop up in your **airodump-ng** console window (like on a <a href="http://img.wonderhowto.com/img/original/27/47/63513197552766/0/635131975527662747.jpg" target="_blank">screenshot</a> (top-right corner) )<br />


# Dependencies
**Following script IS NOT dependent on any library, nor external sources.**<br />

# Requirements
- Wireless adapter which supports injection (see [https://code.google.com/p/reaver-wps/wiki/SupportedWirelessDrivers Reaver Wiki])
- Linux Backtrack 5 
- Root access on your system (otherwise some things may not work)
- AND if you use other Linux distribution
  - Reaver 1.4 (I didn't try it with previous versions)
  - KDE (unless you'll change 'konsole' invocations to 'screen', 'gnome-terminal' or something like that... this is easy)
  - Gawk (Gnu AWK)
  - Macchanger
  - Airmon-ng, Airodump-ng, Aireplay-ng
  - Perl
  

# Additional Info
Before you use this script make sure that your script has permissions to execute.<br />
If not type: <br />
```
chmod +x ./WPA-Attack
```

# Detailed tutorial about WPA/WPA2 Cracking
<a href="http://www.aircrack-ng.org/doku.php?id=cracking_wpa&DokuWiki=c14abd7131d5560715e51eb686263ade">Tutorial: How to Crack WPA/WPA2</a> 

# Successfully cracked WPA Passphrase!
If you manage to crack **WPA passphrase** you should see the following: 
- Aircrack window should output something like
```
KEY FOUND! [ 'mySecretPass' ] 
```        
- Script window should output something like:
```
!!!! KEY WAS FOUND !!!!
---------- YOUR WPA KEY IS: ----------------
mySecretPass
--------------------------------------------
You have it also in file: /root/WPA-Attack/KEY_FOUND_00027255FFC0
```
- There should be also a file like this *KEY_FOUND_00027255FFC0* in current directory

# DONATIONS
Like my project ?   
Want to help in future development, and adding new features ?   
If you find this project useful...  
#### You can <a href="https://sites.google.com/site/dominikdonationbutton/">SUPPORT ME BY PAYPAL</a>
I created PayPal Donation Button as Google Site because here not all HTML tags are allowed and Donation Button HTML can't be put here...  
Every dollar will be appreciated and help me in future development of my projects. 

# Legal Disclaimer
Usage of **WPA Attack** for attacking targets without prior mutual consent is illegal.  
It is the end user's responsibility to obey all applicable local, state and federal laws.  
Developers assume no liability and are not responsible for any misuse or damage caused by this program.

