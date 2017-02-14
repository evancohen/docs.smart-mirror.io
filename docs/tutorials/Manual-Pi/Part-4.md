# Install Manually on Raspberry Pi 2 or 3
### Part 4 - Install Smart-Mirror Dependencies

{% hint style='danger' %}
This guide is only intended for Raspberry 2 or 3. If you're not using a Raspberry Pi 2 or 3
####DO NOT CONTINUE
{% endhint %}

{% hint style='tip' %}
Why are you doing this the hard way? 
There's a much easy tutorial to follow! [Click here to go to that tutorial](/docs/tutorials/install-easily-on-raspberry-pi-2-or-3.md)

If you want to do it the hard way you will get no additional praise or honor. But here's the steps regardless.

[If you would prefer you can also watch the tutorial video for this step here.](#)
{% endhint %}

We are still a long way from running this thing. We have to install the projects dependencies. 

## Step 1 - Make sure you're in the Smart-Mirror Directory
All the commands root of the `smart-mirror` directory run:
```
cd ~/smart-mirror
```

## Step 2 - Run Install Command for Node Package Manager
now that we are in the correct folder we can run the command which will install our dependencies.
```
npm install --loglevel error
```
{% hint style='info' %}
This will take a few minutes, it has to download [electron-prebuilt](https://github.com/mafintosh/electron-prebuilt). Once it is complete please continue to the next part.

You might get warnings when installing and this is fine. Its just letting you know that something is off a bit. Usually it is a dependency that has depreciated and been replaced. the log level of ERROR cannot be ignored as this is something that caused the install to fail... If this happens please visit us on 
But do not fear... We're here. We've all been there... Head over to the [discord chat](https://discord.gg/EMb4ynW) and we'll help you get it all straightened out. and we'll work with you to get it resolved.  
{% endhint %}

<ul class="pager">
  <li class="previous"><a href="Part-3.html">Previous</a></li>
  <li class="next"><a href="Part-5.html">Next</a></li>
</ul>