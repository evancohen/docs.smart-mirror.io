# Install Manually on Linux
### Part 8 - Running the Smart-Mirror

{% hint style='danger' %}
This guide is NOT intended for Raspberry Pi.

This guide is to be used when installing on a linux system. Most common reason for installing on a linux system is for development.

Due to the nature of diverse linux builds, we will keep this very generalized. However, Keep in mind this is done with Ubuntu Desktop in mind. 

####DO NOT CONTINUE
{% endhint %}

{% hint style='tip' %}
[If you would prefer you can also watch the tutorial video for this step here.](#)
{% endhint %}

![](http://i.giphy.com/3otPoS81loriI9sO8o.gif)
#Congratulations! You've completed all the steps!!

Now for some details to assist in running the mirror...

To make the mirror automatically start at boot check out [Part 7 - Final Touches, Option 3 - Start The Mirror on Boot](Part-7.md#option-3---start-the-mirror-on-boot).

## Commands Used to Run Smart-Mirror

Please do not use this page as part of the step by step process. This is more intended as a reference.

#### Starting Smart-Mirror normally
```
npm start
```
#### Starting Smart-Mirror with the dev console
```
npm start dev
```
#### Training a Keyword Spotter Model
```
npm run train-model
```

<ul class="pager">
  <li class="previous"><a href="Part-8.html">Previous</a></li>
</ul>