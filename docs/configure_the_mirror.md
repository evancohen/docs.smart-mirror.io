# Configure the smart-mirror
The smart-mirror is configured using the Remote Configuration Tool. This requires you starting the mirror.

Open the terminal and type:
```
npm start
```

If you're running the mirror for the first time (or for the first time since running upgrading to this version of the mirror) you'll see a QR Code with a URL under it. From a phone or another computer (on the same network as your Smart-Mirror) you can open a browser and manually enter the URL. If you're not running the mirror for the first time and you've properly configured the Sound and Voice, say the keyword/hotword and then "Show Remote Link" to display the URL to reach the Remote Configuration Tool.

After going to the Home page click on Settings > Configure the Mirror.

See below for links to get service keys and example values for config properties. You will have to obtain keys for Forcast.io, YouTube, SoundCloud. If you're using Fitbit you'll need a key for that as well. If you're using Hue Lights with this project you'll need to know the IP address of your Hue Hub and a username. Please go through this slowly, and thoroughly. 

Any issues or questions please join us on [discord chat](https://discord.gg/JDnHaZH).

It is **required** that you [train your own personal model for the keyword](#speech). By training your own model, you increase the samples available so a universal model can be created. Also, this solves many of the issues where the keyword is not detected, as well as false positives.

#### Index
- [Language](#language)
- [Speech](#speech)
- [Layout](#layout)
- [Greeting](#greeting)
- [Forecast](#forecast)
- [Geolocation](#geolocation)
- [Hue](#hue)
- [Calendar](#calendar)
- [Giphy](#giphy)
- [YouTube](#youtube)
- [SoundCloud](#soundcloud)
- [Traffic](#traffic)
- [TV Service](#tvsservice)
- [AutoTimer](#autotimer)
- [Motion](#motion)
- [Fitbit](https://github.com/evancohen/smart-mirror/blob/master/Fitbit-README.md) _(See issue [#350](https://github.com/evancohen/smart-mirror/issues/350) before attempting configuration for fitbit)_


### Language
The following languages are fully supported:
 - `en-XX` - English
 - `de-XX` - German
 - `es-XX` - Spanish
 - `fr-XX` - French
 - `ko-XX` - Korean
 - `pt-XX` - Portuguese

Specific locales can also be specified, by replacing the `XX` above with the country code.

For instance `en-US` for English (United States), `es-AR` for Spanish (Argentina), or `es-BO` for Spanish (Bolivia). For more details about supported speech detection languages see this [Google Cloud Platform Speech API](https://cloud.google.com/speech/docs/languages) page.

### Speech
The speech config object has the following properties:
- `keyFilename` - The location of your JSON keyfile for 
- `keyword` - The text of the keyword that you are using to trigger the mirror. This should be "Smart Mirror". Additional Keywords can be entered by clicking the `+` sign.
- `model` - The filename for your model (should not include spaces). Additional models can be entered by clicking the `+` sign.
- `sensitivity` - Sensitivity for the keyword spotter. This value is between 0 and 1. If you are getting too many false positives or are having trouble detecting you can change this value.

### Layout
You can set these values to be `"main"` (recommended) or `"icesnow"`.

### Greeting
`greeting` can either be an array of greetings to randomly select from OR it can be an object that specifies multiple arrays to choose from based on the time of day.

###### Disable Greeting
You can disable the greeting by selecting `Randomly All Day` for "How would you like greetings displayed?" and then clicking `-` sign to remove any values listed.

###### Randomly Selected Greeting
Select `Randomly All Day` for "How would you like greetings displayed?" and enter as many greetings as you would like by pressing the `+` sign. You can also click on a tab to rearrange the order. Lastly you can click the `-` sign to remove the greeting on the bottom.

###### Randomly Selected Greeting Based On The Time Of Day
Select `By Time of Day` for "How would you like greetings displayed?" and enter as many greetings as you would like for each time of day (Morning, Midday, Evening, and Night) by pressing the `+` sign under each heading. You can also click on a tab to rearrange the order. Lastly you can click the `-` sign to remove the greeting on the bottom.

### Forecast
You'll need a forecast.io developer key, which you can obtain from: https://developer.forecast.io

- `API Key` - After Creating an account you can find your key at the bottom of the page. It should look something like this: `vy2u1t34bo123bu41234yduv1234tb`. Enter this in the `key` field under `Forecast.io API Settings` 
- `Units` - It should be ok to leave the `units` set as auto because the units that are used are determined by your location. If you would like to use other units you can look the [forecast.io documentation](https://developer.forecast.io/docs/v2#options) for more info.
- `Refresh Interval (minutes)` - This is how often you would like the Weather to update in minutes.

### Geolocation
This is an **optional** setting and is only for people who are having issues with the smart-mirror's built in geolocation. You can override your latitude and longitude by entering them here.

### Hue
You'll need two things to set up your Philips Hue configuration, an `ip` and a `username`. You can find the instructions for this on the Philips Hue Documentation site in the [Getting Started](http://www.developers.meethue.com/documentation/getting-started) section (unfortunately you need to create an account to view this info).

Optionally you can create groups (using the API for Philips Hue app) that you can control from the mirror by name. By default group `0` will control all the lights.

### Calendar
You can have the mirror display your iCal's from Google Calendar, Outlook, iCloud, and more by adding them to the `icals` array.

There are two other properties:
- `maxResults`: Maximum number of upcoming calender events to display.
- `maxDays`: Maximum number of days to look into the future when listing upcoming events.

### Giphy
If you want to display gifs on your mirror you can do that too! In the [Giphy Beta API](https://github.com/Giphy/GiphyAPI) the key is fixed `dc6zaTOxFJmzC`

### YouTube
You can find instructions for getting YouTube API Keys here: https://developers.google.com/youtube/v3/getting-started#before-you-start

The key will look similiar to this: `vy2u1t34bo123bu41234yduv1234tb`

### SoundCloud
SoundCloud API keys can be obtained from your app profile (this requires an account): http://soundcloud.com/you/apps

The key will look similiar to this: `vy2u1t34bo123bu41234yduv1234tb`

### Traffic
Using your key from the [Bing Maps Portal](https://www.bingmapsportal.com/Application) you can specify an array of `trips` and a `reload_interval` (how often should the mirror refresh trip data, in minutes).

A trip has the following properties:
- `mode` - Mode of transportation. One of
 -  `"Driving"` - By Car
 -  `"Transit"` - By public transportation
 -  `"Walking"` - Walking
-  `origin` - The address for the start of your trip
-  `destination` - The address for the destination of your trip
-  `name` - Human readable name for the destination
-  `startTime` - Time to start displaying on Smart Mirror. (optional: leave blank to always display) 
-  `endTime` - Time to end displaying on Smart Mirror. (optional: leave blank to always display) 

If any of your trips aren't showing up it's likely because Bing Maps can't find the address you specified. Using a full postal address should fix this issue.


Now that you've configured everything you're ready to save your configuration by clicking save. This will restart the Smart-Mirror.

Next Step (OPTIONAL): [Setting up Smart-Mirror to Run on Boot](setting_up_smart-mirror_to_run_on_boot.md)

### TV Shows

### AutoTimer

### Motion

