# Configuring Sound

> If you have trouble setting up speech recognition try heading over to the [troubleshooting section](troubleshooting.md). If that doesn't work drop into the [discord chat](https://discord.gg/JDnHaZH).

There are two ways to configure audio: 
- [Use a script](#Scripted_Audio_Configuration)
- [Manually configure audio](#Scripted_Audio_Configuration)

### Scripted Audio Configuration

Currently the audio configuration script is not configuring properly.
We will update this documentation when the script is safe to use again.

### Manual Audio input and output Configuration
If you run into issues configuring your audio see the [Troubleshooting your Microphone and Speech Recognition issues](microphone_and_speech_recognition_issues.md) section. To configure your USB microphone and audio output you'll want to determine your playback and recording devices. 

We no longer need to check the playback device as we will always use `hw:0,0` as the playback device. However, we do need to know the recording device.

You'll want to determine the recording device:
```bash
$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 1: Camera [Vimicro USB2.0 UVC Camera], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
Here the recording device is card 1, device 0, or `hw1:0`.


And finally you'll want to replace the contents of your sound config file with `rm -f ~/.asoundrc && nano ~/.asoundrc`:

```bash
pcm.!default {
  type asym
   playback.pcm {
     type plug
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
