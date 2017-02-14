# Install Manually on Raspberry Pi 2 or 3
### Part 5 - Configure the Pi

{% hint style='danger' %}
This guide is only intended for Raspberry 2 or 3. If you're not using a Raspberry Pi 2 or 3
####DO NOT CONTINUE
{% endhint %}

{% hint style='tip' %}
Why are you doing this the hard way? 
There's a much easy tutorial to follow! [Click here to go to that tutorial](/docs/tutorials/install-easily-on-raspberry-pi-2-or-3.md)

If you want to do it the hard way you will get no additional praise or honor. But here's the steps regardless.

[If you would prefer you can also watch the tutorial video for this step here.](#)
{% endhint %}

## Step 1 - Open the User Autostart File to Disable the Screensaver
Edit the **/home/pi/.config/lxsession/LXDE-pi/autostart** file by entering this command into the terminal: 
```bash
nano /home/pi/.config/lxsession/LXDE-pi/autostart
```

## Step 2 - Comment out the Screensaver Line
To disable the screensaver you'll want to comment out (with a `#`) the `@xscreensaver`. 
##### Before (your file might be slightly different)
`@xscreensaver is on line 3 in this example. So, we will edit line 3:
```
@lxpanel --profile LXDE-pi
@pcmanfm --desktop --profile LXDE-pi
@xscreensaver -no-splash
@point-rpi
```
##### After (your file might be slightly different)
After you comment out the line with `@xscreensaver` it will look similar to this:
```
@lxpanel --profile LXDE-pi
@pcmanfm --desktop --profile LXDE-pi
#@xscreensaver -no-splash
@point-rpi
```

## Step 3 - Add the Following Lines to the same file.
next you'll want to add the following to the end of the file.
```
@xset s 0 0
@xset s noblank
@xset s noexpose
@xset dpms 0 0 0
``` 
##### Before (your file might be slightly different)
```
@lxpanel --profile LXDE-pi
@pcmanfm --desktop --profile LXDE-pi
#@xscreensaver -no-splash
@point-rpi
```
##### After (your file might be slightly different)
Finale file will look similar to this:
```
@lxpanel --profile LXDE-pi
@pcmanfm --desktop --profile LXDE-pi
@xscreensaver -no-splash
@point-rpi

@xset s 0 0
@xset s noblank
@xset s noexpose
@xset dpms 0 0 0
```

## Step 4 - Save file
To save the file do the following keystrokes:
press `ctrl` + `x`
then press `y` to confirm changes
then press `enter` to confirm the filename.

## Step 5 - Open the Global Autostart File to Hide the Mouse When Inactive

```
sudo nano /etc/xdg/lxsession/LXDE-pi/autostart
```
{% hint style='info'%}
This is not the same file you just edited in steps 1 - 4.
{% endhint %}

## Step 6 - Add a Line to the Global Autostart File
Then Add the following line to the file you opened in step 5:
```
unclutter -idle 0.1 -root
```

<ul class="pager">
  <li class="previous"><a href="Part-4.html">Previous</a></li>
  <li class="next"><a href="Part-6.html">Next</a></li>
</ul>