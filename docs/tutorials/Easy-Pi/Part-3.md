# Install Easily on Raspberry Pi 2 or 3
### Part 3 - Configure Voice

{% hint style='danger' %}
This guide is only intended for Raspberry 2 or 3. If you're not using a Raspberry Pi 2 or 3 
####DO NOT CONTINUE
{% endhint %}

{% hint style='tip' %}
If you have trouble setting up speech recognition try heading over to the [troubleshooting section](troubleshooting.md). If that doesn't work drop into the [discord chat](https://discord.gg/JDnHaZH).

[If you would prefer you can also watch the tutorial video for this step here.](#)
{% endhint %}

## Step 1 - Setting up Speech Recognition
The smart mirror uses [Sonus](https://github.com/evancohen/sonus) with Google Cloud Speech for keyword spotting and recognition. To set that up, you'll need to create a new project in the Cloud Platform Console:

{% hint style='tip' %}
Google Cloud Platform Console, changes with out notice. This will be updated as we can but this will probably be the trickiest part of this guide. It will require some quick thinking and willingness to ask for help. This is where we shamelessly plug [discord chat](https://discord.gg/JDnHaZH) again. 

Please if you see differences in the console and what's shown here, ask for help in the support section then we can help and update these docs. The contributors don't create new keys often, there's really no need to once the smart-mirror is up and running. We need your feedback and help.
{% endhint %}

1. In the Cloud Platform Console, go to the Projects page and select or create a new project.  
**[GO TO THE PROJECTS PAGE](https://console.cloud.google.com/project)**
2. Enable billing for your project.  
**[ENABLE BILLING](https://support.google.com/cloud/answer/6293499#enable-billing)**
3. Enable the Cloud Speech API.  
**[ENABLE THE API](https://console.cloud.google.com/flows/enableapi?apiid=speech.googleapis.com)** - For more info see [Cloud Speech API Pricing](https://cloud.google.com/speech/#cloud-speech-api-pricing) (for normal smart mirror usage it will be  free)
4. Create a new **JSON service account key** and download it to the `smart-mirror` folder...  
[Credentials Guide: On Your Own Server](https://googlecloudplatform.github.io/google-cloud-node/#/docs/google-cloud/0.42.2/guides/authentication#onyourownserver).

When prompted to create a new service account select "Project Owner"
> ![New service account](/images/new-service-account.png) 

Keep this information for later. You'll need your keyfile to [configure the smart mirror](configure_the_mirror.md#speech).


## Step 2 - Train your own Keyword
Training your own keyword will drastically increase the accuracy of keyword detection. This will be most accurate if you do this on your Pi using the microphone that you'll be using to trigger the mirror.

{% hint style='tip' %}
Here's the deal. You can use any keyword you want. We request you help improve the smart-mirror keyword. After that feel free to improve any other keyword or create your own. Thank you.
{% endhint %}


**From the smart mirror directory run:**
```
npm run train-model
```

This command launches the snowboy site in embedded chromium.
{% hint style='info' %}   
There has been a snowboy bug that may require you to click the logo in the top left, login, close the window, and re-run the command. 

When we last tested this was not an issue however we're leaving this here in case anyone else has this issue so they can solve it easily. 
{% endhint %}

**Or, you can train your model here:** https://snowboy.kitt.ai/hotword/47 

## Step 3 - Download you're model
Once trained, download the model and save it to the root of the smart-mirror directory.

<ul class="pager">
  <li class="previous"><a href="Part-2.html">Previous</a></li>
  <li class="next"><a href="Part-4.html">Next</a></li>
</ul>