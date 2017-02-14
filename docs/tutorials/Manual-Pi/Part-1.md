# Install Manually on Raspberry Pi 2 or 3
### Part 1 - Install Raspbian

{% hint style='danger' %}
This guide is only intended for Raspberry 2 or 3. If you're not using a Raspberry Pi 2 or 3
####DO NOT CONTINUE
{% endhint %}

{% hint style='tip' %}
Why are you doing this the hard way? 
There's a much easy tutorial to follow! [Click here to go to that tutorial](/docs/tutorials/install-easily-on-raspberry-pi-2-or-3.md)

If you want to do it the hard way you will get no additional praise or honor. But here's the steps regardless.

[If you would prefer you can also watch the tutorial video for this step here. Which will use the NOOBs LITE install path. As well as complete any optional steps.](#)
{% endhint %}

## Step 1 - Select Install Path and Install Raspbian Full
To get started we suggest a clean install of Raspbian. You can snag a fresh copy of Jessie w/ Pixel [Raspbian Download Page](https://www.raspberrypi.org/downloads/raspbian/).  
Make sure to download the **Full desktop image**. 

{% hint style='tip' %}
To make things easier you can now use NOOBS to install Raspbian Full. Few things regarding this... 

1. Use NOOBS LITE -- This will require you to be connected to the internet but will also allow you to always install the newest version of Raspbian
2. You still must install Raspbian Full. Don't use Raspbian Lite. There's a lot of differences between the two and its a nightmare getting the mirror running on Lite. 

[If you would prefer you can also watch the tutorial video here. Which will use the NOOBs LITE install path. ](#)
{% endhint %}

After choosing your Raspbian install path. You will either install Raspbian by writing the desktop image to your SD-Card or by Copying the NOOBs LITE files to your SD-Card and then installing via NOOBs LITE. After Raspbian is installed you can move on to Step 2.

## Step 2 - Update Packages
{% hint style='tip' %}
Don't use SSH. First it might be insecure. Second, as of the 2016-11-25 build of Raspbian Jessie, they changed how SSH works and its more complicated to get going so unless you're an advanced user just don't. We will not cover SSH in this tutorial, configure at your own peril. 
{% endhint %}

The next step is to open the terminal within Raspbian and run the following command there

```
sudo apt-get update
sudo apt-get upgrade
```

## The following Steps are Optional
## Option 1 - Install Team Viewer
We highly recommend installing Team Viewer. With a Team Viewer account you can actually login from anywhere.
To install Team Viewer click on [this link](https://pages.teamviewer.com/published/raspberrypi/) from within the browser from your Raspbian Install. (This is also covered in the Video Tutorial for this step.)

## Option 2 - Set-Up File Sharing
You might want to copy files over your network from windows to the Raspberry Pi. Like you might need to copy your keyfile.json file or your keyword personal model file.

To share network folders to a Windows computer we need to install some special software on the Raspberry Pi. The software providing the secret sauce this time is called Samba. The Samba software package implements the SMB protocol and provides support for the Windows naming service (WINS) and for joining a Windows Workgroup.

We can go through how to do this as basics but the steps might be a bit different for your specific network.

### Option 2 Step 1 - Install and configure required software

Installing the software is easy – login to your Raspberry Pi and run:
```bash
sudo apt-get install samba samba-common-bin
```

### Option 2 Step 2 - Install and configure required software
After installation configure the software by opening the file /etc/samba/smb.conf using the command:
```bash
sudo nano /etc/samba/smb.conf
```
Read through the file and make sure you have the following parameters set:
```
workgroup = WORKGROUP
wins support = yes
```
You can use anything as your workgroup name as long as it is alphanumerical and matches the workgroup you would like to join. The default workgroup in Windows 7 is WORKGROUP.

### Option 2 Step 3 - Setup folder to share

Next step is to create the folder you would like to share. To create a folder called “share” in your home directory do the following:
```bash
mkdir ~/share
```

With the folder created we can now tell the Samba software to share it on the network. Open the file /etc/samba/smb.conf using the command:
```bash
sudo nano /etc/samba/smb.conf
```

Scroll to the bottom and add the following:
```
[PiShare]
 comment=Raspberry Pi Share
 path=/home/pi/share
 browseable=Yes
 writeable=Yes
 only guest=no
 create mask=0777
 directory mask=0777
 public=no
```
Notice how we tell Samba that public access is not allowed via “public=no” – this means that anyone wanting to access the shared folder must login with a valid user.

### Option 2 Step 4 - Set remote user password
In this case the valid user is the user called “pi”. To let Samba know that “pi” is a network user run the command:
```bash
sudo smbpasswd -a pi
```
And enter pi’s password twice (default: raspberry).

At this point we can now login to the share from our Windows computer – use Domain: raspberrypi, User: pi and Password: raspberry (unless you changed the password).
{% hint style='tip' %}
Login to shared folder on Raspberry Pi

If you do not want to deal with logging in you can always make the share publicly available by changing the config file to say:
```
public=yes
```
However please note that this is extremely dangerous since anyone will be able to access, modify and delete your files.
{% endhint %}


<ul class="pager">
  <li class="next"><a href="Part-2.html">Next</a></li>
</ul>