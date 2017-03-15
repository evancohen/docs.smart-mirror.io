# Install Manually on Raspberry Pi 2 or 3
### Part 9 - Running the Smart-Mirror

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

![](http://i.giphy.com/3otPoS81loriI9sO8o.gif)
#Congratulations! You've completed all the steps!!

Now for some details to assist in running the mirror...

To make the mirror automatically start at boot check out [Part 4 - Final Touches, Option 4 - Start The Mirror on Boot](Part-4.md#option-4---start-the-mirror-on-boot).

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