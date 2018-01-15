# Configure the Pi

#### Rotate your monitor
To rotate your monitor you'll need to add the following line to **/boot/config.txt** using the following command ```sudo nano /boot/config.txt```
```
display_rotate=1
```
You can also set this value to '3' to have a flipped vertical orientation.

#### Disable screensaver and remove panel
Edit the **/home/pi/.config/lxsession/LXDE-pi/autostart** file with `nano /home/pi/.config/lxsession/LXDE-pi/autostart`.

**Reccomended** To disable the screensaver you'll want to comment out (with a '#') the `@xscreensaver`. You'll also want to add the following lines to that same file
```
@xset s off
@xset -dpms
@xset s noblank
```
**Optional** To remove the panel at the top of the screen to comment out the `@lxpanel` lines. If you want to be able to easily access the "menu" at the top of the screen do not do this step.


#### Hide the mouse when inactive
```
sudo apt-get install unclutter
```
Then Add `unclutter -idle 0.1 -root` to **/etc/xdg/lxsession/LXDE-pi/autostart** with `sudo nano /etc/xdg/lxsession/LXDE-pi/autostart`

Next Step: [Configuring Sound](configuring-sound.md)
