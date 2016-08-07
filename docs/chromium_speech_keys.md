# Configuring Chromium Speech Keys
>### This is no longer optional and should be done as part of the configuration

Because of the high volume smart mirrors being created we have cumulatively been using the Google Speech quota for `electron-prebuilt`.

To solve this problem, we recommend using your own chromium API keys (giving you your own query quota). To get your own keys you'll need to follow the instructions for [Acquiring Keys](https://www.chromium.org/developers/how-tos/api-keys) in the  Chromium developer documentation.
**DO NOT POST QUESTIONS IN THE CHROMIUM DEVELOPER FORUM**, instead ask on the [gitter chat](gitter.im/evancohen/smart-mirror).
 
 
Once you have your `GOOGLE_API_KEY`, `GOOGLE_DEFAULT_CLIENT_ID` and `GOOGLE_DEFAULT_CLIENT_SECRET` you'll need to provide these values at runtime by setting them as environmental variables.

For the Pi you can do this with `nano ~/.profile` and adding the following lines to the end of the file:

```
# Chromium API Keys
export GOOGLE_API_KEY=your_api_key
export GOOGLE_DEFAULT_CLIENT_ID=your_client_id
export GOOGLE_DEFAULT_CLIENT_SECRET=your_client_secret
```

After applying your changes you must restart your pi for them to take effect. Once you've done that you can test these values using `printenv` to display all environmental variables on your Pi. If your keys do not appear ensure 

### Troubleshooting

#### Still getting 'Google Speech Recognizer is down' error
Double check that `printenv` displays the API keys. Check the Google developer console to see if your quota is actually being used. 
>Please note, there are no quotes surrounding your API Keys in the `.profile` file.


#### It worked, but then it stopped. Why?
Currently you can only get 50 requests per day for an app. Check the developer console to see if you have used these requests.

The mirror burns through these requests within minutes when left running. To fix this Evan has utilized [Keyword Spotting](configure_the_mirror.md#speech) to only make requests after a you say "smart mirror". 
>Keyword Spotting is currently only supported on a Raspbery Pi. Although it may work with other operating systems. It is completely unsupported on windows.


