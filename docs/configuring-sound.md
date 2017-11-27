# Configuring Sound

> If you have trouble setting up speech recognition try heading over to the [troubleshooting section](troubleshooting.md). If that doesn't work drop into the [discord chat](https://discord.gg/JDnHaZH).

Hooray! Configuring sound on the mirror is now way easier. When you run the mirror for the first time, you'll be prompted to configure your input device base on available USB devices. Go ahead and skip to [Configuring Speech Recognition](configuring_voice.md).

## Audio Output

Should you want to change the output from AUX \(headphone jack\) to HDMI or back again you can run the following:

To output audio through the headphone jack:

```bash
amixer cset numid=3 1
```

To force the audio back through HDMI you can run:

```bash
amixer cset numid=3 2
```

Next Step: [Configure Speech Recognition](configuring_voice.md)

