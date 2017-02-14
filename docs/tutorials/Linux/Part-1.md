# Install Manually on Linux
### Part 1 - Install Native Dependencies

{% hint style='danger' %}
This guide is NOT intended for Raspberry Pi.

This guide is to be used when installing on a linux system. 

We will keep this very generalized 

####DO NOT CONTINUE
{% endhint %}

{% hint style='danger' %}
If you have already ran the Install Script from [Install Easily on Raspberry Pi 2 or 3 >> Part 2 - Run Install Script](/docs/tutorials/Easy-Pi/Part-2.md) 

Then, don't do this part. Its already been done. You've also, managed to change tutorials some how.
####DO NOT CONTINUE
{% endhint %}

{% hint style='tip' %}
Why are you doing this the hard way? 
There's a much easy tutorial to follow! [Click here to go to that tutorial](/docs/tutorials/install-easily-on-raspberry-pi-2-or-3.md)

If you want to do it the hard way you will get no additional praise or honor. But here's the steps regardless.

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
  <li class="previous"><a href="Part-1.html">Previous</a></li>
  <li class="next"><a href="Part-3.html">Next</a></li>
</ul>