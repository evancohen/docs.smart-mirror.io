# Install Raspbian

**These instructions are specific to the Raspberry Pi 2 and 3**

To get started I suggest a clean install of Raspbian. You can snag a fresh copy of Jessie w/ Pixel [Raspbian Download Page](https://www.raspberrypi.org/downloads/raspbian/).
Make sure to download the **Full desktop image**. Do not use NOOBS to install Raspbian. 

For instructions on how to install Raspbian see [How To Install Raspbian(full)](docs/howto/how_to_install_raspbianfull.md).

You'll also need to install Node (v6.x) which now comes bundled with npm.
```
curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
sudo apt-get install -y nodejs
```

##### Getting the code
Next up you'll want to clone this repository into your user's home folder on your Pi:
```
cd ~
git clone https://github.com/evancohen/smart-mirror.git
```

Next Step: [Install Dependencies](install_dependencies.md)

