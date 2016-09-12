# Start the mirror on boot

Optionally, you can configure your Pi to start the mirror on boot. There is a script in the **/smart-mirror/scripts** folder called **bash-start.sh**. We will copy that file to the **/home/pi** folder. 
```
cd ~
cp ./smart-mirror/scripts/bash-start.sh smart-start.sh
```

Make the file owned by the user pi
```
chown pi:pi /home/pi/smart-start.sh
chmod +x /home/pi/smart-start.sh
```

Then, edit the file **/home/pi/.config/lxsession/LXDE-pi/autostart**
and add the following line to the end:
`/home/pi/smart-start.sh &`
Reboot the Pi and you should be good to go
