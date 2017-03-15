# Install Manually on Linux
### Part 1 - Install Native Dependencies

{% hint style='danger' %}
This guide is NOT intended for Raspberry Pi.

This guide is to be used when installing on a linux system. Most common reason for installing on a linux system is for development.

Due to the nature of diverse linux builds, we will keep this very generalized. However, Keep in mind this is done with Ubuntu Desktop in mind. 

####DO NOT CONTINUE
{% endhint %}

{% hint style='tip' %}
[If you would prefer you can also watch the tutorial video for this step here.](#)
{% endhint %}

## Step 1 - Open Terminal Window
Open the terminal in Raspbian. 

## Step 2 - Enter Command to Install Native Dependencies
```bash
sudo apt-get install -y curl wget git unclutter libatlas-base-dev
```
{% hint style='info' %}
A word about the `sudo` command. This command is used to elevate the user rights for other commands and run those commands as `root` user. This can cause issues if you use it for everything as not everything is designed to be installed or to be ran as `root`. Only use this command when instructed to in this tutorial.

When we run `sudo apt-get install` we are running the command `apt-get install` as `root`. I think of it as `sudo` is actually saying **S**uper **U**ser **DO** (command). 
{% endhint %}


<ul class="pager">
  <li class="next"><a href="Part-2.html">Next</a></li>
</ul>