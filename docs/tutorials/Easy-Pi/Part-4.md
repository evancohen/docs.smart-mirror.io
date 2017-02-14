# Install Easily on Raspberry Pi 2 or 3
### Part 4 - Final Touches

{% hint style='danger' %}
This guide is only intended for Raspberry 2 or 3. If you're not using a Raspberry Pi 2 or 3 
####DO NOT CONTINUE
{% endhint %}

### All of These Final Touches are optional.

* [Option 1 - Rotate your monitor](/docs/tutorials/Easy-Pi/Part-4.md#option-1---rotate-your-monitor)
* [Option 2 - Audio Input and Output Configuration](/docs/tutorials/Easy-Pi/Part-4.md#option-2---audio-input-and-output-configuration)
* [Option 3 - Force Raspberry Pi Audio Output](/docs/tutorials/Easy-Pi/Part-4.md#option-3---force-raspberry-pi-audio-output)
* [Option 4 - Start the mirror on boot](/docs/tutorials/Easy-Pi/Part-4.md#option-4---start-the-mirror-on-boot)

{% hint style='tip' %}
[If you would prefer you can also watch the tutorial video for this step here.](#)
{% endhint %}

## Option 1 - Rotate your monitor
To rotate your monitor you'll need to add the following line to **/boot/config.txt** using the following command ```sudo nano /boot/config.txt```
```
display_rotate=1
```
You can also set this value to '3' to have a flipped vertical orientation. 

## Option 2 - Audio Input and Output Configuration
{% hint style='tip' %}
With the latest version of Smart-Mirror you shouldn't have to do this step. Its here for previous user's that need to look up the old way of doing this.

This will step will require a reboot afterwards
{% endhint %}


### Option 2 Step 1 - List Capture Devices
Then you'll want to determine the recording device:
``` bash
$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 1: Camera [Vimicro USB2.0 UVC Camera], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
Here the recording device is card 1, device 0, or `hw1:0`.

### Option 2 Step 2 - Replace/Edit .asoundrc file
And finally you'll want to replace the contents of your sound config file. To do this enter the following command in the Raspbian Terminal:

``` bash 
rm -f ~/.asoundrc && nano ~/.asoundrc`:
```

### Option 2 Step 3 - Enter .asoundrc file content
Then copy and paste the following into the terminal. You'll have to change the "hw:x:x" values to the values your determined in Option 2 Step 1:
``` bash
pcm.!default {
  type asym
   playback.pcm {
     type plug
     # This is your output device (In this case AUX out on the Pi)
     slave.pcm "hw:0,0"
   }
   capture.pcm {
     type plug
     # This is your input device (it may be different from what is seen here)
     slave.pcm "hw:1,0"
   }
}
```
{% hint style='danger' %}
If you refer to issue [#471](https://github.com/evancohen/smart-mirror/issues/471) You'll see that this is updated instructions based on the results we've seen regarding this issue. the playback.pcm settings will always be "hw:0:0". 
{% endhint %}

## Option 3 - Force Raspberry Pi Audio Output
{% hint style='tip' %}
You will only have to do this step if you're not getting audio out the desired onboard audio card.

This will step will require a reboot afterwards
{% endhint %}

**Note**: In order to push audio through the headphone jack, You must also run:
``` bash
amixer cset numid=3 1
```
To force the audio back through HDMI you can run:
``` bash
amixer cset numid=3 2
```

after finishing that enter: 
``` bash
sudo reboot
```

{% hint style='tip' %}
This can also be done by entering the following command into the terminal:  
``` bash
sudo raspi-config
```

1. then select `8 - Advanced Settings` 
2. then select `A9 Audio` 
3. then Select either 
  * `1 - Force 3.5mm ('headphone') jack` or
  * `2 - Force HDMI`

after finishing that enter: 
``` bash
sudo reboot
```
{% endhint %}

## Option 4 - Start the mirror on boot

Optionally, you can configure your Pi to start the mirror on boot. 

### Option 4 Step 1 - Copy Start Script
There is a script in the ```/smart-mirror/scripts``` folder called ```bash-start.sh```. We will copy that file to the ```/home/pi``` folder. 

``` bash
cd ~
cp ./smart-mirror/scripts/bash-start.sh smart-start.sh
```

### Option 4 Step 2 - Change Ownership and Make File Executable
Make the file owned by the user pi
```
chown pi:pi /home/pi/smart-start.sh
chmod +x /home/pi/smart-start.sh
```

### Option 4 Step 3 - Run the Script at Start-Up 
Then, edit the file by entering the following into the terminal:
``` bash
sudo nano /home/pi/.config/lxsession/LXDE-pi/autostart
``` 
Then add the following line to the end:
```
/home/pi/smart-start.sh &
```
When you next reboot the Pi and you should be good to go

<ul class="pager">
  <li class="previous"><a href="Part-3.html">Previous</a></li>
  <li class="next"><a href="Part-5.html">Next</a></li>
</ul>