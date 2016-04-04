# Chromium Speech Keys
### [This is optional]

Because of the high volume smart mirrors being created we have cumulatively been using the Google Speech speech quota for `electron-prebuilt`.

To solve this problem, we recommend using your own chromium API keys (giving you your own query quota). To get your own keys you'll need to follow the instructions for [Acquiring Keys](https://www.chromium.org/developers/how-tos/api-keys) in the  Chromium developer documentation.

Once you have your `GOOGLE_API_KEY`, `GOOGLE_DEFAULT_CLIENT_ID` and `GOOGLE_DEFAULT_CLIENT_SECRET` you'll need to provide these values at runtime by setting them as environmental variables. For the Pi you can do this by adding the following lines to the end of `~/.profile`:

```
# Chromium API Keys
GOOGLE_API_KEY=your_api_key
GOOGLE_DEFAULT_CLIENT_ID=your_client_id
GOOGLE_DEFAULT_CLIENT_SECRET=your_client_secret
```

To test that these values were set you can use `printenv` to display all environmental variables on your Pi. If your keys do not appear you may need to reboot your device.