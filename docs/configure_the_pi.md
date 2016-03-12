# Configure the Pi

##### Rotate your monitor
To rotate your monitor you'll need to add the following line to `/boot/config.txt`
```
display_rotate=1
```
You can also set this value to '3' to have a flipped vertical orientation.

##### Disable screensaver
To disable the screensaver you'll want to comment out (with a '#') the `@xscreensaver` and `@lxpanel` lines in `/etc/xdg/lxsession/LXDE/autostart`. You'll also want to add the following lines to that same file
```
@xset s off
@xset -dpms
@xset s noblank
```
##### Start the mirror on boot
Optionally, you can configure your Pi to start the mirror on boot
In **/home/pi/**, create the file called smart-start.sh with the following content:
```
#!/bin/bash
export DISPLAY=:0
export XAUTHORITY=/home/pi/.Xauthority
cd /home/pi/smart-mirror && npm start
```

Make the file owned by the user pi
`chown pi:pi /home/pi/smart-start.sh`
And make it executable
`chmod +x /home/pi/smart-start.sh`
Then, edit the file **/home/pi/.config/lxsession/LXDE-pi/autostart**
and add the following line to the end:
/`home/pi/smart-start.sh &`
Reboot the Pi and you should be good to go

Next step: [Install dependencies and run](install_dependencies_and_run.md)