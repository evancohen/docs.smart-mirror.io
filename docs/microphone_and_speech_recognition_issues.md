# Microphone and Speech Recognition issues

># `WARNING: This is not complete.`
#####It will be updated soon :)

Most of these issues can be fixed by following the following:

1. Have you [installed all necessary dependencies](install_dependencies.md)?
2. Is your microphone [configured correctly](configure_the_pi.html#audio-input-and-output)?

If you've done these and are still having issues I would recommend running `npm start dev` and seeing what (if any) error you get after you say "smart mirror".

### If saying "smart mirror" does nothing or you see a light glowing on the bottom but no other command works:
There is likely an issue with Sonus. You can run it from the `smart-mirror` directory with:

``` bash
npm run sonus
```
##### Testing Speech Using Sonus
When you start Sonus in the terminal, you will see this:
```
$ npm run sonus

> smart-mirror@0.0.9 sonus /home/bmartin/smart-mirror
> node sonus.js

█ 
```
When you see the blinking cursor, this means that Sonus is listening. Now you would say the command, "smart mirror, show me how to tie a bow tie" You're results should be similar to this:

```
!h: 1
!p: show
!p: show me
!p: show me a
!p: show me how
!p: show me how to
!p: show
!p: show me
!p: show me how to
!p: show me how to
!f: show me how to tie a bow tie
```
#### Let's break these results down

###### Confirming the Hotword is Detected.
When you say "smart mirror" if you've installed all dependencies correctly, trained your model, and configured the Speech Settings correctly on the Remote ConfigUI. You should get a `!h: 1` response. This is saying that the hotword was detected correctly. If you have more than one hotword you'll get a response `!h: x` where `x` is the index number of the hotword specified in the Remote ConfigUI. 

If you don't see anything displayed when saying "smart mirror" then the most common issues are:
- `~/.asoundrc` isn't configured properly. [Follow steps to configure sound here.](/docs/configuring-sound.md)
- Personal Model file (commonly named `smart_mirror.pmdl`) is missing from the `smart-mirror` folder, or isn't entered correctly on Remote ConfigUI. This file can be named anything you would like as long as there's no spaces, and it is correctly entered on Remote ConfigUI. [Follow Steps for Speech Settings here.](/docs/configure_the_mirror.md#speech)
- Personal Model isn't trained. [Follow steps for training your own model here.](/docs/configuring_voice.md)
- Dependencies aren't properly installed. [follow steps here.](/docs/install_dependencies.md) 

###### Confirming Google Speech API is configured correctly.
Assuming you're getting a response that the hotword is detected. You then would say the command. In our example above that command is "show me how to tie a bow tie". While the audio is streaming to Google Speech API you will get partial results. This is shown in the examples starting with `!p: ` followed by the partial transcribed result. After it has completed transcribing the command a final results response is received. This is shown in the examples starting with `!f: ` followed by the final transcribed result. If you're getting partial and final results, then speech recognition is working for you. 

If you see the response for the hotword, but no partial or final results, then the most common issues are:
- Google Cloud Speech API key JSON file (commonly named `keyfile.json` is missing from the `smart-mirror` folder, or isn't entered correctly on Remote ConfigUI. The `keyfile.json` file can be named anything you would like as long as it has no spaces, and it is correctly entered on Remote ConfigUI. [Follow Steps for Speech Settings here.](/docs/configure_the_mirror.md#speech)
- Billing is either not enabled, project is not attached to the billing account, or billing account is closed within the Google Cloud Platform. [Follow the steps for configuring voice here.](/docs/configuring_voice.md)


**Still having issues?** Check out [recent audio related issues on GitHub](https://github.com/evancohen/smart-mirror/issues?utf8=%E2%9C%93&q=is%3Aissue%20audio%20-label%3A%22status%3A%20Outdated%20Issue%20-%20Informational%20Only%22%20).

**Also,** we're available on [discord chat](https://discord.gg/EMb4ynW) to help assist you in real time.
