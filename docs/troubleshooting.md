# Troubleshooting

##### Microphone issues
This is the definitive answer to all of your problems (hopefully). There is no need to mess around with ALSA conf files. All you have to do is run:

```
sudo aptitude install pulseaudio
```
Then, optionally, if you want to force sound out of the headphone jack:
```
sudo modprobe snd_bcm2835
sudo amixer cset numid=3 1
```
Or, to get sound over HDMI:
```
sudo modprobe snd_bcm2835
sudo amixer cset numid=3 0
```
A reboot is required after this.

##### Mirror won't start
The mirror can not be started via `npm start` over ssh, however you can run the "run on boot" script to start the mirror remotely.