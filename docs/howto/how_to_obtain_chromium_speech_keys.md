# How To Obtain Chromium Speech Keys

Acquiring Keys

1. Make sure you are a member of chromium-dev@chromium.org (you can just subscribe to chromium-dev and choose not to receive mail). 
> For convenience, the APIs below are only visible to people subscribed to that group.
2. Make sure you are logged in with the Google account associated with the email address that you used to subscribe to chromium-dev.
3. Go to https://cloud.google.com/console
Click the blue `Create Project` button.
4. (Optional) You may add other members of your organization or team on the Team tab.
5. In the 'APIs & auth' > APIs tab -> API Library tab, search for all of the following APIs. If you're a member of the chromeos-dev Google group you should see all of them. For each of these APIs click on them when found by the search, and then click on "Enable API" button at the top, read and agree to the Terms of Service that is shown, check the "I have read and agree to <API name> Terms of Service" checkbox and click Accept: 
(This list might be out of date; try searching for APIs starting with "Chrome" or having "for Chrome" in the name.)
* Calendar API
* Contacts API
* Drive API (Optional, enable this for Files.app on Chrome OS and SyncFileSystem API)
* Chrome Remote Desktop API
* Chrome Spelling API
* Chrome Suggest API
* Chrome Sync API
* Chrome Translate Element
* Chrome Web Store API
* Chrome OS Hardware ID API (Optional, Chrome OS)
* Device Registration API (Optional, Chrome OS)
* Google Clound DNS API
* Google Cloud Storage
* Google Cloud Storage JSON API
* Google Maps Geolocation API 
(requires enabling billing but is free to use; you can skip this one, in which case geolocation features of Chrome will not work)
* Google Maps Time Zone API
* Google Now For Chrome API (Optional, enabled to show Google Now cards)
* Google+ API
* Nearby Messages API
* Safe Browsing API
* Speech API **(NOT Google Cloud Speech API)**
