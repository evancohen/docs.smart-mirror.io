# Configuring Sound

> If you have trouble setting up speech recognition try heading over to the [troubleshooting section](troubleshooting.md). If that doesn't work drop into the [discord chat](https://discord.gg/JDnHaZH).

There are two ways to configure audio: 
- [Use a script](#Scripted_Audio_Configuration)
- [Manually configure audio](#Scripted_Audio_Configuration)

### Scripted Audio Configuration

Currently the audio configuration script is not configuring properly.
We will update this documentation when the script is safe to use again.
<!--
Running this script makes configuration easier but you must not enter invalid input. Entering invalid input will make the script fail currently with little to no indication that it has failed. Having said that, if you have a 
```
cd ~/smart-mirror
./scripts/conf-audio.sh
```
Now with the remote configuration. We should be able to implement audio configuration via that platform until then, we have the above bash script to help you. If this doesn't work out for you, or you're feeling a bit old school please follow the steps below.

Afterwards, you will need to do [this.](#Final_Configuration_Step_Regardless_of_Scripted_or_Manual_Configuration_Above)
-->

### Manual Audio input and output Configuration
If you run into issues configuring your audio see the [Troubleshooting your Microphone and Speech Recognition issues](microphone_and_speech_recognition_issues.md) section. To configure your USB microphone and audio output you'll want to determine your playback and recording devices. 

First, you'll want to check the available playback devices
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


And finally you'll want to replace the contents of your sound config file with `rm -f ~/.asoundrc && sudo nano /etc/asound.conf`:

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

## Final Configuration Step Regardless of Scripted or Manual Configuration Above

**Note**: In order to push audio through the headphone jack, setting `hw:0,0` is not enough. You must also run:
``` bash
amixer cset numid=3 1
```
To force the audio back through HDMI you can run:
``` bash
amixer cset numid=3 2
```

Next Step: [Configuring Voice](configuring_voice.md)
