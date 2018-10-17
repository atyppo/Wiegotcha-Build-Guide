# Wiegotcha Build Guide
The guide created by Mike Kelly at exfil.co is much more succinct if you are already experienced. I recommend supplementing this guide with Mike's to fully understand this build if you are a beginner. This was my first time using Raspberry Pi at all. All hardware and software design can be found there as well. All credits go to Mike for his furtherance of this project, which was originally created by Bishop Fox. I live in a small dorm, so usage of tools in this guide is kept to a bare minimum. If you see any mistakes or have any suggestions for this guide, please let me know. 

## What I used in my build:

##### HID 5375 Long-Range Reader (~$100-$250 used on eBay)
I recommend purchasing this used on eBay. Some search terms to use include "5375AGN00," "maxiprox" and "HID 5375."
I purchased a brand new reader. I managed to find a seller who was willing to sell one with an offer for $250, which is at the upper end of what used readers sell for, so I decided to purchase a new reader instead.

##### Raspberry Pi 3 Model 3 ($34.99 w/ Amazon-provided discount as of 10/16/18)
This is what's used to interpret the info from the reader and create a Wi-Fi network to view the stolen credentials. More info available in Mike's post at exfil.co.

##### Tabiger Soldering Iron Kit ($16.96 as of 10/16/18)
I didn't originally think I would need this, since this guide was intended to be solder-free. The level converters I purchased appeared to be pre-soldered but were not when I received them. You may not need this if you already have one or are able to find pre-soldered ones. 
Please send me a link if you find pre-soldered level converters!

Amazon link: https://www.amazon.com/gp/product/B01H1IFT54/ref=oh_aui_detailpage_o03_s00?ie=UTF8&psc=1 

##### 3.3V-5V Level Converters ($7.99 as of 10/16/18)
Although these appear to already be soldered in the product image, THEY ARE NOT. However, at $1.60 each (this is a pack of five), they are incredibly cheap, and useful four extras if you're inexperienced at soldering.

Amazon link: https://www.amazon.com/gp/product/B07DCVFYJT/ref=oh_aui_detailpage_o08_s00?ie=UTF8&psc=1

##### Battery Pack with USB and 5V Output ($33.99 as of 10/16/18)
Not much to say here. Battery pack comes with a charger and a Y-cable to power the reader's board. I used pre-spliced cables because of my limited access to tools. Micro-USB cable needed to power the Pi.

Amazon link: https://www.amazon.com/gp/product/B00ME3ZH7C/ref=oh_aui_detailpage_o09_s00?ie=UTF8&psc=1

##### 5V Pre-Spliced Cables ($7.99 as of 10/16/18)
These are entirely optional. You'll only need one of the male cables (five of them come with this item). I used these because I did not have access to a tool to splice cable. If you do, I suggest simply using the Y-cable that comes with the battery pack.

Amazon link: https://www.amazon.com/gp/product/B07BP5RDLR/ref=oh_aui_detailpage_o07_s00?ie=UTF8&psc=1

##### Micro-USB Cable ($8.99 as of 10/16/18)
I used a 3-foot braided cable for durability. There are lots of cheaper options out there if you'd prefer. I'm not sure if a foot-long cable would be long enough. 

Amazon link: https://www.amazon.com/gp/product/B074VM7J6B/ref=oh_aui_detailpage_o08_s01?ie=UTF8&psc=1

##### Jumper Wires ($6.98 as of 10/16/18)
You'll use 5 Female to Female and 3 Male to Female wires. Reference the diagram in Mike's post for better instructions on wiring it. 

Amazon link: https://www.amazon.com/gp/product/B01EV70C78/ref=od_aui_detailpages00?ie=UTF8&psc=1

##### Real Time Clock ($8.99 as of 10/16/18)
This device is used to calibrate the clock so accurate timestamps are printed when 192.168.150.1 is accessed. 

Amazon link: https://www.amazon.com/gp/product/B00HF4NUSS/ref=oh_aui_detailpage_o08_s01?ie=UTF8&psc=1

##### 16GB MicroSD Card ($6.80 as of 10/16/18)
Not much to say here. When you receive the card, format to FAT format. Card must be at least 8GB in size. I chose 16GB in case I needed extra storage.

Amazon link: https://www.amazon.com/gp/product/B004ZIENBA/ref=oh_aui_detailpage_o09_s00?ie=UTF8&psc=1

##### Vibrating Motor ($5.22 as of 10/16/18)
Entirely optional. It causes the reader to vibrate instead of emit a noise when a card is read. This can be found cheaper elsewhere, but I tried to include as many Amazon links as possible to make it simple to order everything. I purchased it, but chose not to install it because I am not experienced at soldering. Mike's post details how to install this.

Amazon link: https://www.amazon.com/gp/product/B00OKCPXOC/ref=oh_aui_detailpage_o08_s01?ie=UTF8&psc=1

##### Velcro ($5.10 as of 10/16/18)
Also entirely optional. However, I strongly recommend purchasing for use on the battery pack and Pi so they don't slide around. I attached three strips on the back of my battery pack and one on the back of my Pi. 

Amazon link: https://www.amazon.com/gp/product/B00006IC2L/ref=oh_aui_detailpage_o09_s00?ie=UTF8&psc=1


## How I Built It:

1) In my case, I received the parts before I received the reader. I assembled these first, then simply added them to the reader once I received it. Therefore, this guide will follow that method. It could certainly be assembled in a different order if desired.

2) Solder the header pins to the level converter.

3) Connect the jumper wires to the header pins on the level converter, then connect to the header pins on the Raspberry Pi. Use Mike's diagram found [here.](https://i2.wp.com/exfil.co/wp-content/uploads/2017/01/diagram.gif?ssl=1) I highly recommend using the same colors he uses for simplicity.

4) Plug the SD Card into your computer. Format it as a FAT card. I was not able to do this without opening Command Prompt for whatever reason. I'm running Windows 10. I used `Format /FS:FAT [INSERT YOUR DRIVE LETTER WITH COLON HERE]`

5) Download the image (found under Step 1 of Easy Mode) from the Github repository found [here.](https://github.com/lixmk/Wiegotcha) I unzipped it using 7zip. I used Win32 Disk Imager to write the image to the SD card. Select the image file, then select the FAT-formatted SD Card's Drive Letter. 

6) Place the MicroSD card in your Pi. Connect the Raspberry Pi to the Micro-USB cable and the battery pack (or other acceptable power source). Turn it on by powering the battery pack. Give it a minute or two to boot up.

7) Connect to the Wi-Fi network "Wiegotcha" with the password "Wiegotcha." The default SSID and password should be changed immediately, along with the root usernames and passwords. This can be done by using a program like PuTTY. Choose a SSH connection using an IP address of 192.168.150.1 and 22 as your port. All other values should be left to their defaults. Log in as root with Wiegotcha as your password. To change the Wi-Fi network's name and password, use the command `nano Wiegotcha/confs/hostapd.conf`. This command is case-sensitive. Modify the values of ssid and wpa_passphrase to their desired values. To change the root password, use the command `sudo passwd root`. Connect the Pi with an Ethernet connection, then use the command `/root/Wiegotcha/fixclock.sh` to calibrate the Real-Time Clock. 

8) Connect a spliced male 5V cable to ports 1 and 3 of the "TB1" terminal. Make sure that the red wire connects to port 1 and the black (ground) wire connects to port 3. Then, connect the black jumper wire as shown in the diagram to TB1's Port 2. Connect the green and white jumper wires to ports 1 and 2 (respectively) of the TB2 terminal.

9) Place your Raspberry Pi and level shifters in their desired positions. I suggest affixing the Pi inside of the reader with Velcro and taping down any stray cables with duct tape. I find Gorilla Tape to work the best, however, you can use whatever you'd like. Then, connect to the battery pack with the Micro-USB cable and male 5V cable. I suggest affixing the battery pack to the back of the reader with Velcro. 

10) Put dip switch 4 in the SW1 set of switches in the off (down) position if you wish for the reader to not beep (it will regardless upon startup) when reading cards. This needs to be turned on if you wish for it to vibrate. 

11) Once this is done, visit 192.168.150.1 with your preferred browser and test with a card to ensure everything works. If the proper facility code and serial number shows up, you're done! You can use the hex value to clone this badge using a Proxmark 3. 
