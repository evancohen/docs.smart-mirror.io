# Install Smart Mirror dependencies

You'll need to install the following in order to run the keyword spotter and have the mirror listen to you:
```
sudo apt-get install sox
```

Before we can run the thing we've got to install the projects dependencies. From the root of the `smart-mirror` directory run:
```
cd ~/smart-mirror
npm install
```

This will take a few minutes, it has to download [electron-prebuilt](https://github.com/mafintosh/electron-prebuilt). Once it is complete please continue to configuring the smart-mirror.

Next Step: [Configure the Pi](configure_the_pi.md)