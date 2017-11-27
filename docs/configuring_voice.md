# Configure Speech Recognition

> If you have trouble setting up speech recognition try heading over to the [troubleshooting section](troubleshooting.md). If that doesn't work drop into the [discord chat](https://discord.gg/JDnHaZH).

The smart mirror uses \[Sonus\]\(https://github.com/evancohen/sonus\) for speech recognition. The following steps will get you everything you need to make this work:

## Setting up Speech Recognition

The smart mirror uses [Sonus](https://github.com/evancohen/sonus) with Google Cloud Speech for keyword spotting and recognition. To set that up, you'll need to create a new project in the Cloud Platform Console:

1. In the Cloud Platform Console, go to the Projects page and select or create a new project.  
   [**GO TO THE PROJECTS PAGE**](https://console.cloud.google.com/project)
2. Enable billing for your project.  
   [**ENABLE BILLING**](https://support.google.com/cloud/answer/6293499#enable-billing)
3. Enable the Cloud Speech API.  
   [**ENABLE THE API**](https://console.cloud.google.com/flows/enableapi?apiid=speech.googleapis.com) - For more info see [Cloud Speech API Pricing](https://cloud.google.com/speech/#cloud-speech-api-pricing) \(for normal smart mirror usage it will be  free\)
4. Create a new **JSON service account key** and download it to the `smart-mirror` folder...  
   [Credentials Guide: On Your Own Server](https://googlecloudplatform.github.io/google-cloud-node/#/docs/google-cloud/0.42.2/guides/authentication#onyourownserver).

When prompted to create a new service account select "Project Owner"

> ![New service account](new-service-account.png)

Keep this information for later. You'll need your projectID and keyfile to [configure the smart mirror](configure_the_mirror.md#speech).

## \[Optional\] Train your own Keyword

**Note:** This is no longer required, the mirror comes with a pre-trained universal model! If you're having trouble with the universal model you can follow these steps

Training your own keyword will drastically increase the accuracy of keyword detection. This will be most accurate if you do this on your Pi using the microphone that you'll be using to trigger the mirror.

**From the smart mirror directory run:**

```
npm run train-model
```

**Or, you can train your model here:** [https://snowboy.kitt.ai/hotword/47](https://snowboy.kitt.ai/hotword/47)

Once trained, download the model and save it to the root of the smart-mirror directory.

Next Step: [Run The Mirror For the First Time](/first_time_running_smart_mirror.md)

