# Troubleshooting

### Issues installing electron-prebuilt
You must run `npm install` when logged into the GUI and not over ssh as electron-prebuilt will not install outside of the GUI.

### Microphone and Speech Recognition issues
Most of these issues can be fixed by following the following:

1. Have you [installed all necessary dependencies](http://docs.smart-mirror.io/docs/installation.html#installing-smart-mirror-dependencies)?
2. Have you created [chromium speech keys](docs/chromium_speech_keys.html)?
3. Is your microphone [configured to stream to multiple sources simultaneously](http://docs.smart-mirror.io/docs/configure_the_pi.html#audio-input-and-output)?

If you've done all three of those things and are still having issues I would recommend running `npm start dev` and seeing what (if any) error you get after you say "smart mirror".

**If saying "smart mirror" does nothing:**
There is likely an issue with the keyword spotter. You can run it from the `smart-mirror` directory with
``` bash
python speech/kws.py smart_mirror.pmdl 0.5
```
If *that* doesn't work and you've installed all dependencies then the spotter may not be recognizing your voice. You can train the model on your pi on the latest `dev` branch by running `npm run train-model`. More info in #330.

**Still not getting the keyword "smart mirror" to work:**
Run `npm start dev` and then manually trigger speech recognition by putting the following into the dev tools:
``` javascript
annyang.start()
```

**If you get a `network` error:**
Something is probably wrong with step 2 above. Double check that this is configured correctly and follow the [troubleshooting steps](http://docs.smart-mirror.io/docs/chromium_speech_keys.html#troubleshooting) if you get stuck. Keep in mind that the speech keys should not be enclosed in quotes in the `.profile` file.

**If you get an `audio-capture` error:**
This is likely an issue with step 3. To test your microphone you can run 
``` bash
npm run microphone-debug
```
Note: that this will not be streaming to multiple processes, you can simulate this by running the python command mentioned above from another terminal tab.
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

> ###NOTE: A reboot is required after this.

**Still having issues?** Check out [recent audio related issues on GitHub](https://github.com/evancohen/smart-mirror/issues?utf8=%E2%9C%93&q=is%3Aissue%20audio).

### Mirror won't start
The mirror can not be started via `npm start` over ssh, however you can run the "run on boot" script to start the mirror remotely.
