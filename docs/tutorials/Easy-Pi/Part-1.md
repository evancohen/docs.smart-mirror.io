# Install Easily on Raspberry Pi 2 or 3
### Part 1 - Install Raspbian

{% hint style='danger' %}
This guide is only intended for Raspberry 2 or 3. If you're not using a Raspberry Pi 2 or 3
####DO NOT CONTINUE
{% endhint %}

{% hint style='tip' %}
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

After choosing your Raspbian install path. You will either install Raspbian by writing the desktop image to your SD-Card or by Copying the NOOBs LITE files to your SD-Card and then installing via NOOBs LITE. After Raspbian is installed you can move on to [Step 2](/docs/tutorials/Easy-Pi/Part-1.md#step-2).

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

## Option 2 - TBD


<ul class="pager">
  <li class="next"><a href="Part-2.html">Next</a></li>
</ul>