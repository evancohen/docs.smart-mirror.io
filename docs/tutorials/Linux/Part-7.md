# Install Manually on Linux
### Part 7 - Final Touches

{% hint style='danger' %}
This guide is NOT intended for Raspberry Pi.

This guide is to be used when installing on a linux system. Most common reason for installing on a linux system is for development.

Due to the nature of diverse linux builds, we will keep this very generalized. However, Keep in mind this is done with Ubuntu Desktop in mind. 

####DO NOT CONTINUE
{% endhint %}

{% hint style='tip' %}
[If you would prefer you can also watch the tutorial video for this step here.](#)
{% endhint %}

### All of These Final Touches are optional.

* [Option 1 - Rotate your monitor](/docs/tutorials/Linux/Part-7.md#option-1---rotate-your-monitor)
* [Option 2 - Audio Input and Output Configuration](/docs/tutorials/Linux/Part-7.md#option-2---audio-input-and-output-configuration)
* [Option 3 - Start the mirror on boot](/docs/tutorials/Linux/Part-7.md#option-3---start-the-mirror-on-boot)

{% hint style='tip' %}
[If you would prefer you can also watch the tutorial video for this step here.](#)
{% endhint %}

## Option 1 - Rotate your monitor
{% hint style='tip' %}
This step is how we would do this in raspbian. If you're using the linux system for development you might not want to do this. A bit of googling though might help you find how to do it for your version of linux. Note this probably is the wrong way to do this for most Linux Systems.

Regardless, This will step will require a reboot afterwards.
{% endhint %}

To rotate your monitor you'll need to add the following line to **/boot/config.txt** using the following command ```sudo nano /boot/config.txt```
```
display_rotate=1
```
You can also set this value to '3' to have a flipped vertical orientation. 

## Option 2 - Audio Input and Output Configuration
{% hint style='tip' %}
With the latest version of Smart-Mirror you shouldn't have to do this step. It's here for previous user's that need to look up the old way of doing this. Also, This step should really not at all be required for a linux system however it would most likely be the same steps. A bit of googling though might help you find how to do it for your version of linux.

This will step will require a reboot afterwards.
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

## Option 3 - Start the mirror on boot

Optionally, you can configure your Linux System to start the mirror on boot.

{% hint style='tip' %}
This step is how we would do this in raspbian. If you're using the linux system for development you might not want to do this. A bit of googling though might help you find how to do it for your version of linux. Note this probably is the wrong way to do this for most Linux Systems.

Regardless, This will step will require a reboot afterwards.
{% endhint %}

 

### Option 3 Step 1 - Copy Start Script
There is a script in the ```/smart-mirror/scripts``` folder called ```bash-start.sh```. We will copy that file to the ```/home/pi``` folder. 

``` bash
cd ~
cp ./smart-mirror/scripts/bash-start.sh smart-start.sh
```

### Option 3 Step 2 - Change Ownership and Make File Executable
Make the file owned by the user pi
```
chown pi:pi /home/pi/smart-start.sh
chmod +x /home/pi/smart-start.sh
```

### Option 3 Step 3 - Run the Script at Start-Up 
Then, edit the file by entering the following into the terminal:
``` bash
sudo nano /home/pi/.config/lxsession/LXDE-pi/autostart
``` 
Then add the following line to the end:
```
/home/pi/smart-start.sh &
```
When you next reboot the System and you should be good to go

<ul class="pager">
  <li class="previous"><a href="Part-6.html">Previous</a></li>
  <li class="next"><a href="Part-8.html">Next</a></li>
</ul>