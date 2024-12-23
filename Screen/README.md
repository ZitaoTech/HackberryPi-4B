# This page will tell you the ways to install the display driver in different operating system and some using tips of the display  
### First you need to install the operating system you need into RaspberryPi, this is the [tutorial](https://www.raspberrypi.com/documentation/computers/getting-started.html#installing-the-operating-system), when you choose device, select Raspberry Pi4.  
### There are 2 micro-HDMI ports on the top side of HackberryPi4B. You can connect it with another screen. You can use the following commands to disable/enable the displaying.

```sh
vcgencmd display_power 0
vcgencmd display_power 1
```
### The default backlight brightness of the display after you turn HackberryPi on would be 50%. There is a physical button of the top side of HackberryPi. You can single press it to toggle the backlight of the display. You can also adjust the backlight brightness by long pressing the button: If you first long press the button the backlight brightness will slowly increase to 100%, if you now release the button and long press the button again, the backlight brightness of the display will slowly drop to 10%.  
# Raspberry Pi OS after 04/04/2022 or later  

Add the following line in `/boot/config.txt` in your TF card  

```sh
dtoverlay=vc4-kms-dpi-hyperpixel4sq
``` 
And the `config.txt` file will look like this:  
![image](https://github.com/user-attachments/assets/33139e0d-2477-4732-8ff5-a3e2bce9d383)  
Follow the steps:  
Insert the TF card in to the slot  
Turn on the HackberryPi4B, the screen will be black, wait until the left green led on board stop blinking. that will take about 30 seconds.  
Turn off the HackberryPi and reboot.  
And then your HackberryPi will run Raspberry Pi OS on the screen.  

# Kali Linux or Raspberry Pi OS before 04/04/2022   

### Step 1  
Add the following lines in `/boot/config.txt` in your TF card  

```sh
dtoverlay=hyperpixel4
overscan_left=0
overscan_right=0 
overscan_top=0
overscan_bottom=0
framebuffer_width=720
enable_dpi_lcd=1
display_default_lcd=1
dpi_group=2
dpi_mode=87
dpi_output_format=0x5f026
dpi_timings=720 0 20 20 40 720 0 15 15 15 0 0 0 60 0 36720000 4
```
And the `config.txt` file will look like this:  
![image](https://github.com/user-attachments/assets/eb698c68-0dce-4346-9013-562dcafa3381)

### Step 2  
Download the `hyperpixel4.dtbo`file in this github page   
Put the `hyperpixel4.dtbo`file into `/boot/overlays`folder  
Now you can insert the TF card in to the slot and your HackberryPi will run Kali Linux on the screen.  
