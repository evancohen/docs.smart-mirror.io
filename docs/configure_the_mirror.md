# Configure the smart-mirror

The smart-mirror is configured using the Remote Configuration Tool. This requires you starting the mirror.

Open the terminal and type:

```
npm start
or
pm2 start smart-mirror (if you selected yes to use pm2 to manage starting during install)
```

There are 2 ways to find the IP and port of the remote for the mirror:

### From the command line

When the mirror starts it will output the remote IP and port to the command line:

```
> smart-mirror@0.0.27 start /Users/evan/Git/smart-mirror
> electron main.js

Remote listening on http://192.168.1.130:8080
```

### From a QR code

If you're running the mirror for the first time \(or for the first time since running upgrading to this version of the mirror\) you'll see a QR Code with a URL under it. From a phone or another computer \(on the same network as your Smart-Mirror\) you can open a browser and manually enter the URL.

If you're not running the mirror for the first time and you've properly configured the Sound and Voice, say the keyword/hotword and then "Show Remote Link" to display the URL to reach the Remote Configuration Tool.

## Update Settings

After going to the Home page of the remote, click on Settings &gt; Configure the Mirror.

It is **required** that you fill out Speech Settings!

See below for links to get service keys and example values for config properties. You will have to obtain keys for the following functions
  Weather,
  YouTube,
  SoundCloud,
  Fitbit,
  Geolocation,
  Maps,
  Spotify
   If you're using Hue Lights with this project you'll need to know the IP address of your Hue Hub and a username. Please go through this slowly, and thoroughly.

Any issues or questions please join us on [discord chat](https://discord.gg/JDnHaZH).

#### Index

* [Language](#language)
* [Speech](#speech)
* [Layout](#layout)
* [Greeting](#greeting)
* [weather](#weather)
* [Geolocation](#geolocation)
* [Hue](#hue)
* [Calendar](#calendar)
* [Giphy](#giphy)
* [YouTube](#youtube)
* [SoundCloud](#soundcloud)
* [Stock](#stock)
* [Traffic](#traffic)
* [TV Service](#tvsservice)
* [AutoTimer](#autotimer)
* [Motion](#motion)
* [Fitbit](https://github.com/evancohen/smart-mirror/blob/master/Fitbit-README.md) _\(See issue _[_\#350_](https://github.com/evancohen/smart-mirror/issues/350)_ before attempting configuration for fitbit\)_

### Language

The following languages are fully supported:

* `en-XX` - English
* `de-XX` - German
* `es-XX` - Spanish
* `fr-XX` - French
* `ko-XX` - Korean
* `pt-XX` - Portuguese

Specific locales can also be specified, by replacing the `XX` above with the country code.

For instance `en-US` for English \(United States\), `es-AR` for Spanish \(Argentina\), or `es-BO` for Spanish \(Bolivia\). For more details about supported speech detection languages see this [Google Cloud Platform Speech API](https://cloud.google.com/speech/docs/languages) page.

### Speech

The speech config object has the following properties:

* `keyFilename` - The location and name of your JSON keyfile for
* `hotword` - The text of the hotword that you are using to trigger the mirror. This should be "Smart Mirror". Additional Keywords can be entered by clicking the `+` sign.
* `model` - The filename for your model \(should not include spaces\). Additional models can be entered by clicking the `+` sign.
* `sensitivity` - Sensitivity for the keyword spotter. This value is between 0 and 1. If you are getting too many false positives or are having trouble detecting you can change this value.

### Layout

You can set these values to be `"main"` \(recommended\) or `"icesnow"`.

### Greeting

`greeting` can either be an array of greetings to randomly select from OR it can be an object that specifies multiple arrays to choose from based on the time of day.

###### Disable Greeting

You can disable the greeting by selecting `Randomly All Day` for "How would you like greetings displayed?" and then clicking `-` sign to remove any values listed.

###### Randomly Selected Greeting

Select `Randomly All Day` for "How would you like greetings displayed?" and enter as many greetings as you would like by pressing the `+` sign. You can also click on a tab to rearrange the order. Lastly you can click the `-` sign to remove the greeting on the bottom.

###### Randomly Selected Greeting Based On The Time Of Day

Select `By Time of Day` for "How would you like greetings displayed?" and enter as many greetings as you would like for each time of day \(Morning, Midday, Evening, and Night\) by pressing the `+` sign under each heading. You can also click on a tab to rearrange the order. Lastly you can click the `-` sign to remove the greeting on the bottom.

### weather

You'll need a an API yet

currently Darksky is no longer giving out free api keys. existing keys will expire sometime near the end of 2021

we have two additional services
Climacell
or
OpenWeather

all services require an api key

* `API Key` - see the links in the `API Key source` dropdown
* `Units` - It should be ok to leave the `units` set as auto because the units that are used are determined by your location.
 if u want to force a particular unit setting select one from the dropdown (US or si)
* `Refresh Interval (minutes)` - This is how often you would like the Weather to update in minutes.
## note that some services limit the number of calls allowed per day , the dropdown provides some reasonable choices from 5 to 60 minutes

### Geolocation

Starting in 2019, the Google Geolocation API used for this feature **requires** an API key.
The entry of your Latitude/Longitude location is still **optional** even tho the API key is **required**.
See the API Key steps in [Configuring Voice](/docs/configuring_voice.md)

This API key also is used in the Map feature

Entering the latitude and longitude is for people who are having issues with the smart-mirror's built in geolocation. You can override your latitude and longitude by entering them here.

### Hue

You'll need two things to set up your Philips Hue configuration, an `ip` and a `username`. You can find the instructions for this on the Philips Hue Documentation site in the [Getting Started](http://www.developers.meethue.com/documentation/getting-started) section \(unfortunately you need to create an account to view this info\).

Optionally you can create groups \(using the API for Philips Hue app\) that you can control from the mirror by name. By default group `0` will control all the lights.

### Calendar

You can have the mirror display your iCal's from Google Calendar, Outlook, iCloud, and more by adding them to the `icals` array. Note that these URLs should begin with `http(s)://` and not `ical://`

There are two other properties:

* `maxResults`: Maximum number of upcoming calender events to display.
* `maxDays`: Maximum number of days to look into the future when listing upcoming events.

### Giphy

If you want to display gifs on your mirror you can do that too! In the [Giphy Beta API](https://github.com/Giphy/GiphyAPI) the key is fixed `dc6zaTOxFJmzC`

### YouTube

You can find instructions for getting YouTube API Keys here: [https://developers.google.com/youtube/v3/getting-started\#before-you-start](https://developers.google.com/youtube/v3/getting-started#before-you-start)

The key will look similiar to this: `vy2u1t34bo123bu41234yduv1234tb`

### Stock

You'll need a AlphaVantage API Key, which you can obtain from: [https://www.alphavantage.co/support/#api-key)

* `API Key` - After selecting from the provided fields, and entering your email address,  you can find your key at the bottom of the page. It should look something like this: `QKQYHF247BBS6Q3V`. Enter this in the `key` field under `Stock Settings, Alpha Vantage API Key`

### SoundCloud

SoundCloud API keys can be obtained from your app profile \(this requires an account\): [http://soundcloud.com/you/apps](http://soundcloud.com/you/apps)

The key will look similiar to this: `vy2u1t34bo123bu41234yduv1234tb`

### Note: Soundcloud is currently not  granting new api keys (Jan 2020)

### Traffic

Using your key from the [Bing Maps Portal](https://www.bingmapsportal.com/Application) you can specify an array of `trips` and a `reload_interval` \(how often should the mirror refresh trip data, in minutes\).

A trip has the following properties:

* `mode` - Mode of transportation. One of
  * `"Driving"` - By Car
  * `"Transit"` - By public transportation
  * `"Walking"` - Walking
* `origin` - The address for the start of your trip
* `destination` - The address for the destination of your trip
* `name` - Human readable name for the destination
* `startTime` - Time to start displaying on Smart Mirror. \(optional: leave blank to always display\)
* `endTime` - Time to end displaying on Smart Mirror. \(optional: leave blank to always display\)

If any of your trips aren't showing up it's likely because Bing Maps can't find the address you specified. Using a full postal address should fix this issue.

Now that you've configured everything you're ready to save your configuration by clicking save. This will restart the Smart-Mirror.

Next Step \(OPTIONAL\): [Setting up Smart-Mirror to Run on Boot](setting_up_smart-mirror_to_run_on_boot.md)

### TV Shows

Simply list the TV shows you would like to display on the mirror and the Mirror will display when the next episode airs if the information is known.

### AutoTimer

Setting up the mirror to go to sleep is easy. Just enter the mode, wait time \(in minutes\), if you want the mirror to turn on at the same time everyday enter the autoWake time in 24 hr format.

##### TV Mode

TV mode will just make the screen go dark... it doesn't actually "power off" this is used on TVs hence being TV mode. Many TVs will show a "no input" message of some sort when using monitor mode. So this makes it work for the people using that type of display device.

##### Monitor Mode

Monitor Mode sends a "sleep status" to the screen and stops sending a signal. In most monitors that will have the monitor go into a "sleep mode". If you're getting a "no input" message of some sort. Change the Mode to TV and see how that works.

> When in monitor mode you must also fill out the commands to go to sleep or to wake the mirror. the default are as follows:
>
> For "Command used to wake up Smart Mirror"
>
> ```
> sudo ./scripts/raspi-monitor.sh on > /dev/null 2>&1
> ```
>
> For "Command used put Smart Mirror to sleep"
>
> ```
> sudo ./scripts/raspi-monitor.sh off > /dev/null 2>&1
> ```

### Motion

Motion allows you to enable a PIR device on your Raspberry Pi. Please refer to the detailed instructions for [Enabling Motion Detection](/docs/enabling-motion-detection.md).

you can also allow an external service of some sort to signal motion, if you have somethign else.  an Example is the use the linux [Motion project](https://motion-project.github.io/motion_guide.html) to manage alerting to motion from a camera, by selecting External as a choice.

the external service needs to call the provided /home/pi/smart-mirror/scripts/external_motion script with a parameter
  started - signal motion detected
  ended   - motion no longer detected

  - ## note that the Motion project signaller runs as root, so the full path to the script above will need to be specified

###  Plugin Location information
starting  in version 0.27, a new configuration feature allows one to position plugin output in any of the defined locations via dropdown selection,
and also disable plugin display if not wanted

if new plugins are installed (there are some), the default display location is bottom center, just above the bottom bar info. to place the modules, create a new entry (+) fill in the plugin name (the folder it is in) and select the location where it should be displayed...  then press submit to restart smart-mirror with this layout..  you can change the layout as many times as you wish, by changing the location dropdown for any/some/all plugins and then pressing submit..
## Note:
one this to note: if you uncheck the Active checkbox on a currently running plugin, its configuration information will be lost.. and will have to be entered again, it the Active checked is selected in the future..
### save any info.
