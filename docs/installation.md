# Installation

**This instructions are specific to the Raspberry Pi 2 and 3**

To get started I suggest a clean install of Raspbian. You can snag a fresh copy of Jessie (recommended, it's the future) or Wheezy from the [Raspbian Download Page](https://www.raspberrypi.org/downloads/raspbian/).
Make sure to download the **Full desktop image**. Do not use NOOBS to install Raspbian. 

For instructions on how to install Raspbian see [Installing Operating System Images](https://www.raspberrypi.org/documentation/installation/installing-images/).

You'll also need to install Node (v6.x) which now comes bundled with npm.
```
curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
sudo apt-get install -y nodejs
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
