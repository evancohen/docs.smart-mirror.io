# Configure the Pi

#### Expand root partition
When you first install Raspbian onto an SD card it doesn't use all the disk space. To reclaim that space run:
```
sudo raspi-config
```
And then choose "Expand root partition to fill SD card" option.

#### Audio input and output
If you run into issues configuring your audio see the [Troubleshooting your Microphone and Speech Recognition issues](troubleshooting.md#microphone_and_speech_recognition_issues) section. To configure your USB microphone and audio output you'll want to determine your playback and recording devices. 

``` bash
$ aplay -l
 **** List of PLAYBACK Hardware Devices ****
 card 0: ALSA [bcm2835 ALSA], device 0: bcm2835 ALSA [bcm2835 ALSA]
   Subdevices: 8/8
   Subdevice #0: subdevice #0
   Subdevice #1: subdevice #1
   Subdevice #2: subdevice #2
   Subdevice #3: subdevice #3
   Subdevice #4: subdevice #4
   Subdevice #5: subdevice #5
   Subdevice #6: subdevice #6
   Subdevice #7: subdevice #7
 card 0: ALSA [bcm2835 ALSA], device 1: bcm2835 ALSA [bcm2835 IEC958/HDMI]
   Subdevices: 1/1
   Subdevice #0: subdevice #0
```
Here the playback device is card 0, device 0, or `hw:0,0` (`hw:0,1` is HDMI audio out).

Then you'll want to determine the recording device:
``` bash
$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 1: Camera [Vimicro USB2.0 UVC Camera], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
Here the recording device is card 1, device 0, or `hw1:0`.


And finally you'll want to update your sound config file with `nano ~/.asoundrc`:

``` bash
#asym fun start here. we define one pcm device called "pluged"
pcm.pluged {
    type plug
    #this is your output device
    slave.pcm "hw:0,1"
}

#one called "dsnooped" for capturing
pcm.dsnooped {
    ipc_key 1027
    type dsnoop
    #this is your input device
    slave.pcm "hw:1,0"
}

#and this is the real magic
pcm.asymed {
    type asym
    playback.pcm "pluged"
    capture.pcm "dsnooped"
}

#a quick plug plugin for above device to do the converting magic
pcm.pasymed {
    type plug
    slave.pcm "asymed"
}

#a ctl device to keep xmms happy
ctl.pasymed {
    type hw
    card 0
}

#for aoss:
pcm.dsp0 {
    type plug
    slave.pcm "asymed"
}

ctl.mixer0 {
    type hw
    card 0
}

pcm.!default {
    type plug
    slave.pcm "asymed"
}
```

> #### Note that this requires a reboot to take effect.

#### Rotate your monitor
To rotate your monitor you'll need to add the following line to **/boot/config.txt** using the following command ```sudo nano /boot/config.txt```
```
display_rotate=1
```
You can also set this value to '3' to have a flipped vertical orientation. 

#### Disable screensaver and remove panel
Edit the **/home/pi/.config/lxsession/LXDE-pi/autostart** file with `nano /home/pi/.config/lxsession/LXDE-pi/autostart`.
* (RECCOMMENDED) To disable the screensaver you'll want to comment out (with a '#') the `@xscreensaver`. You'll also want to add the following lines to that same file
```
@xset s off
@xset -dpms
@xset s noblank
```
* (OPTIONAL) To remove the panel at the top of the screen to comment out the `@lxpanel` lines. If you want to be able to easily access the "menu" at the top of the screen do not do this step.
 

#### Hide the mouse when inactive
```
sudo apt-get install unclutter
```
Then Add `unclutter -idle 0.1 -root` to **/etc/xdg/lxsession/LXDE-pi/autostart** with `sudo nano /etc/xdg/lxsession/LXDE-pi/autostart`

Next Step: [Configure the smart-mirror](configure_the_mirror.md)
