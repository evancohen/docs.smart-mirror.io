# How To Obtain Chromium Speech Keys
![](/docs/stop.png)
># `WARNING: This is no longer required`
#####It is being kept here for legacy reasons

##Enabling API Libraries


1. Make sure you are a member of [chromium-dev@chromium.org](https://groups.google.com/a/chromium.org/forum/?fromgroups#!forum/chromium-dev)  (you can just [subscribe](https://groups.google.com/a/chromium.org/forum/?fromgroups#!forum/chromium-dev) to chromium-dev and choose not to receive mail). 
> For convenience, the APIs below are only visible to people subscribed to that group.
2. Make sure you are logged in with the Google account associated with the email address that you used to subscribe to chromium-dev.
3. Go to https://cloud.google.com/console
4. Click the blue `Create Project` button.
5. (Optional and unlikely for this project) You may add other members of your organization or team on the Team tab.
6. In the `APIs & auth` >> `APIs tab` >> `API Library tab`, search for all of the following APIs. If you're a member of the chromeos-dev Google group you should see all of them. For each of these APIs click on them when found by the search, and then click on "Enable API" button at the top, read and agree to the Terms of Service that is shown, check the "I have read and agree to API name "Terms of Service" checkbox and click Accept: 
(This list might be out of date; try searching for APIs starting with "Chrome" or having "for Chrome" in the name.)
  * Calendar API
  * Contacts API
  * Drive API ***(Optional, enable this for Files.app on Chrome OS and SyncFileSystem API)***
  * Chrome Remote Desktop API
  * Chrome Spelling API
  * Chrome Suggest API
  * Chrome Sync API
  * Chrome Translate Element
  * Chrome Web Store API
  * Chrome OS Hardware ID API ***(Optional, Chrome OS)***
  * Device Registration API ***(Optional, Chrome OS)***
  * Google Clound DNS API
  * Google Cloud Storage
  * Google Cloud Storage JSON API
  * Google Maps Geolocation API 
>>(requires enabling billing but is free to use; you can skip this one, in which case geolocation features of Chrome will not work). 
>> Entering your `geoPosition` in `config.js` will be required if you don't enable billing.
  * Google Maps Time Zone API
  * Google Now For Chrome API ***(Optional, enabled to show Google Now cards)
  * Google+ API
  * Nearby Messages API
  * Safe Browsing API
  * Speech API ***(NOT Google Cloud Speech API)***
  * YouTube Data API ***(You can use the same API key for YouTube and might as well add that library now)***

> If any of these APIs are not shown, recheck step 1.

##Acquiring Keys
1. Go to the Credentials tab under the APIs & auth tab.
- Click the "Add credentials" button then click on the "OAuth 2.0 client ID" item in the drop-down list.
  - Click on the "Configure consent screen" button. Fill in the "Product name" (name it anything you want) and other details if you have available then click on "Save" at the bottom. 
  - Return to the Credentials tab and click the "Add credentials" button again, then select "OAuth 2.0 client ID" from the drop-down list.
  - In the "Application type" section check the "Other" option and give it a name in the "Name" text box, then click "Create"
- In the pop-up window that appears you'll see a client ID  and a "client secret" string. Copy and paste those in a text file on your dev box then click OK to dismiss it.
  - A new item should now appear in the "OAuth 2.0 client IDs" list. You can click on the name of your client id to retrieve the ID and secret at any time. In the next sections, we will refer to the values of the “Client ID” and “Client secret” fields.
- Click the "Add credentials" button again on the same page. 
  - In the pop-over window that shows up click the "Browser key" button.
  - Click on the "API key" item in the drop down list.
  - Fill in the name of the key or leave the default string there. 
  - Leave the "Accept requests from these HTTP referrers (web sites) empty.
  - Click the "Create" button.
  - A pop-over should show up giving you the API key. Copy and paste it in a text file to save it, although you can access it later as well.
  - Click OK to dismiss this.

You should now have an API key and a OAuth 2.0 client ID in on the Credentials tab. The next sections will refer to the value of the “API key” field too.
> Note that the keys you have now acquired are not for distribution purposes and must not be shared with other users.