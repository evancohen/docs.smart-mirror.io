#Enabling for Motion Detection

![](/docs/stop.png)
># `WARNING: Only compatible with Raspberry Pi`
#####Do not enable or attempt to install on any thing other than a Smart-Mirror compatible Raspberry Pi Device. 

### Installing Dependencies

Motion Detection requires Johnny-five.io as well as Raspi-io.

make sure you're within the smart-mirror folder.
```
cd ~/smart-mirror
```

from the smart-mirror folder run the following command.
```
npm install johnny-five && npm install raspi-io
```


### Configuration

Use the Motion Settings of the ConfigUI to configure and enable the motion detection after installing dependencies.

Variable | Usage | Data Type | Default Value if not included in config.js
---------|-------|-----------|--------------
pin | Identify GPIO input Pin connected to output pin of the PIR device or other device used to detect motion | string | GPIO26
enabled | enable motion detection | boolean | false

### Making it all work
##### Parts required

- [PIR Device](https://smile.amazon.com/gp/product/B00FDPO9B8/ref=oh_aui_search_detailpage?ie=UTF8&psc=1)
- (optional!) LED (color of your choice)
- (optional!) Resistor (based on draw of LED) 

##### Wiring Diagram with LED
![figure 1](/assets/Smart-Mirror_Motion_bb_withLED.png)`[figure 1]`
##### Wiring Diagram without LED
![figure 2](/assets/Smart-Mirror_Motion_bb.png) `[figure 2]`

### Basic Functionality

Motion detection works with AutoTimer Settings. Using Johnny-Five's motion API the PIR device is connected to a PIN on the Raspberry Pi. Suggested PIN is GPIO 26 as illustrated in figure 1 and figure 2 above. When the `motionstart` event is triggered the `auto-sleep timer` is stopped and will remain stopped until the `motionend` event is triggered. When the `motionend` event is triggered the `auto-sleep timer` is started and set to the `config.autoTimer.autoSleep` interval set in configUI.

### Issues

A live chat to get help and discuss mirror related issues: https://gitter.im/evancohen/smart-mirror. Usually there are a few folks hanging around in the lobby, but if there arent you are probubly better off [filing an issue](https://github.com/evancohen/smart-mirror/issues/new). Please tag @justbill2020 on any motion detection issues. 