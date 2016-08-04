# Installation

**This instructions are specific to the Raspberry Pi 2 and 3**

To get started I suggest a clean install of Raspbian. You can snag a fresh copy of Jessie (recommended, it's the future) or Wheezy from the [Raspbian Download Page](https://www.raspberrypi.org/downloads/raspbian/).
Make sure to download the **Full desktop image**. Do not use NOOBS to install Raspbian.

You'll also need to install Node (v4.4.3+) which now comes bundled with npm.
```
wget https://nodejs.org/dist/v4.4.3/node-v4.4.3-linux-armv7l.tar.gz 
tar -xvf node-v4.4.3-linux-armv7l.tar.gz 
cd node-v4.4.3-linux-armv7l
```
Copy to /usr/local
```
sudo cp -R * /usr/local/
```

##### Installing smart mirror dependencies
You'll also need to install the following in order to run the keyword spotter and have the mirror listen to you:
```
sudo apt-get install python-pyaudio python3-pyaudio sox
```

##### Getting the code
Next up you'll want to clone this repository into your user's home folder on your Pi:
```
cd ~
git clone https://github.com/evancohen/smart-mirror.git
```

Next Step: [Configure the smart-mirror](configure_the_mirror.md)
