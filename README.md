# CGM Display
CGM Display Project

Always on CGM Display.  Designed for Raspberry Pi using Adafruit's PiTFT Plus 3.5" display (parts list I used below).
This depends on Dexcom CGM data from the Dexcom server.

# Credits

Thanks to jerm's Dexcom Tools project (https://github.com/jerm/dexcom_tools) for the core code used here.

# Parts List

Raspberry Pi Zero W (Should work with any current Raspberry Pi Model.  I got mine from Adafruit (https://www.adafruit.com/product/3400)
Adafruit PiTFT Plus 3.5" Touchscreen display (https://www.adafruit.com/product/2441)
Hammer Header Male - Solderless Raspberry Pi Connector (https://www.adafruit.com/product/3662)

# Requirements
This is the version I developed on.  All required packages were included in the distribution below.  Except for the PiTFT install which is documented below.

Raspberry Pi Version:

"Raspian"
pi@raspberrypi:~ $ cat /etc/debian_version
9.4

pi@raspberrypi:~ $ cat /etc/os-release
PRETTY_NAME="Raspbian GNU/Linux 9 (stretch)"
NAME="Raspbian GNU/Linux"
VERSION_ID="9"
VERSION="9 (stretch)"
ID=raspbian
ID_LIKE=debian
HOME_URL="http://www.raspbian.org/"
SUPPORT_URL="http://www.raspbian.org/RaspbianForums"
BUG_REPORT_URL="http://www.raspbian.org/RaspbianBugs"

Python (Python 2 not supported)
pi@raspberrypi:~ $ sudo python3 --version
Python 3.5.3

# Installation
- Follow the PiTFT software installation instructions: https://learn.adafruit.com/adafruit-pitft-3-dot-5-touch-screen-for-raspberry-pi/easy-install-2
- Download this zip file.  Unzip in your /home/pi directory (all instructions will assume this location).
- Modify /home/pi/cgm_display/cgm_display.ini and put your Login name and password.  These are the ones you use in your Dexcom share app (not follow).  Save the file.
- To run as a foreground application "cd ~/cgm_display ; sudo python3 cgm_display.py"

- To install it to run at boot up automatically add the following line to your startup script.  'sudo nano /etc/rc.local'
sudo python3 /home/pi/cgm_display/cgm_display.py --username=USERNAME --password=PASSWORD --logging=INFO& > /var/log/cgm_display.log 2>&1
 (Note: use --logging=DEBUG for debug level logging)
