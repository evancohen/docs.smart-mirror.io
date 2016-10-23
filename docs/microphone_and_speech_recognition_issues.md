# Microphone and Speech Recognition issues

># `WARNING: This is not complete.`
#####It will be updated soon :)

Most of these issues can be fixed by following the following:

1. Have you [installed all necessary dependencies](install_dependencies.md)?
2. Is your microphone [configured correctly](configure_the_pi.html#audio-input-and-output)?

If you've done these and are still having issues I would recommend running `npm start dev` and seeing what (if any) error you get after you say "smart mirror".

### If saying "smart mirror" does nothing:
There is likely an issue with the keyword spotter. You can run it from the `smart-mirror` directory with
``` bash
node sonus.js smart_mirror.pmdl en-US 0.5
```
If *that* doesn't work and you've installed all dependencies then the spotter may not be recognizing your voice. You can train the model on your pi on the latest `dev` branch by running `npm run train-model`. More info in #330.

**Still having issues?** Check out [recent audio related issues on GitHub](https://github.com/evancohen/smart-mirror/issues?utf8=%E2%9C%93&q=is%3Aissue%20audio).
