# Configure the smart-mirror

The smart-mirror relies on a configuration file to determine what data to display. 

You'll need to create a `config.js` file in the root of your smart-mirror directory. Also in this directory is a configuration template called `config.example.js`. Copy the template and save it as `config.js`.
```
cp config.example.js config.js
```

Then fill out `config.js`. See below for links to get service keys and example values for config properties.

It is **highly recommended** that you [train your own personal model for the keyword](#speech). By training your own model, you increase the samples available so a universal model can be created. Also, this solves many of the issues where the keyword is not detected.
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
- [Fitbit](https://github.com/evancohen/smart-mirror/blob/master/Fitbit-README.md)
- [Motion](#motion)


### Language
The following languages are fully supported:
 - `"en-US"` - English
 - `"de-DE"` - German
 - `"es-ES"` - Spanish
 - `"fr-FR"` - French
 - `"ko-KO"` - Korean

Specific locals can also be specified, for instance `"es-AR"` or `"es-BO"`. For more details about supported speech detection languages see this [Stack**Overflow**](http://stackoverflow.com/questions/14257598/what-are-language-codes-for-voice-recognition-languages-in-chromes-implementati/14302134#14302134) post.

### Speech
Training your own keyword will drastically increase the accuracy of keyword detection. This will be most accurate if you do this on your Pi using the microphone that you'll be using to trigger the mirror.

**You can train your own model here**: https://snowboy.kitt.ai/hotword/47 

Once trained, download the model and save it to the root of the smart-mirror directory.

The speech config object has the following properties:
- `keyword` - The text of the keyword that you are using to trigger the mirror. This should be "Smart Mirror"
- `model` - The filename for your model (should not include spaces)
- `sensitivity` - Sensitivity for the keyword spotter. If you are getting too many false positives or are having trouble detecting you can change this value.
- `continuous` - After detecting a keyword:
 -  `false`: listen to a single utterance (recommended)
 -  `true`: listen until silence is detected (will use lots of speech requests)

### Layout
You can set these values to be `"main"` (recommended) or `"icesnow"`.

### Greeting
`greeting` can either be an array of greetings to randomly select from OR it can be an object that specifies multiple arrays to choose from based on the time of day.

###### Disable Greeting
You can disable the greeting by setting it to an array with an empty string:
``` javascript
greeting: [""]
```
###### Randomly Selected Greeting

``` javascript
greeting : ["Hi, sexy!", "Hey There!", "Looking Awesome!"]
```
###### Randomly Selected Greeting Based On The Time Of Day
``` javascript
greeting : {
    night:    ["Goodnight", "Time to sleep"],
    morning:  ["Good Morning"],
    midday:   ["Good Afternoon"],
    evening:  ["Good evening"]
}
```
### Forecast
You'll need a forecast.io developer key, which you can obtain from: https://developer.forecast.io

After Creating an account you can find your key at the bottom of the page. In your config it should look something like this:

``` javascript
forecast : {
    key : "vy2u1t34bo123bu41234yduv1234tb", // Your forecast.io api key
    units : "auto" // See forecast.io documentation if you are getting the wrong units
}
```
It should be ok to leave the units set as auto because the units that are used are determined by your location. If you would like to use other units you can look the [forecast.io documentation](https://developer.forecast.io/docs/v2#options) for more info.

### Geolocation
This is an **optional** setting and is only for people who are having issues with the smart-mirror's built in geolocatin. You can override your latitude and longitude by specifying the following:
``` javascript
geo_position: {
    latitude: 78.23423423,
    longitude: 13.123124142
}
```

### Hue
You'll need two things to set up your Philips Hue configuration, an `ip` and a `username`. You can find the instructions for this on the Philips Hue Documentation site in the [Getting Started](http://www.developers.meethue.com/documentation/getting-started) section (unfortunately you need to create an account to view this info).

Optionally you can create groups (using the API for Philips Hue app) that you can control form the mirror by name. By default group `0` will control all the lights.

``` javascript
hue : {
    ip : "192.168.1.1",
    uername : "",
    groups : [{
        id : 0,
        name : "all"
    }, {
        id : 1,
        name : "bedroom"
    }, {
        id : 2,
        name : "kitchen"
    }]
}
```

### Calendar
You can have the mirror display your iCal's from Google Calendar, Outlook, iCloud, and more by adding them to the `icals` array.

There are two other properties:
- `maxResults`: Maximum number of upcoming calender events to display.
- `maxDays`: Maximum number of days to look into the future when listing upcoming events.

``` javascript
calendar: {
    icals : ["https://calendar.google.com/calendar/ical/SOMESTUFF/basic.ics",
"https://outlook.office365.com/owa/calendar/SOMESTUFF/reachcalendar.ics"],
    maxResults: 9, 
    maxDays: 365 
}
```

### Giphy
If you want to display gifs on your mirror you can do that too! In the [Giphy Beta API](https://github.com/Giphy/GiphyAPI) the key is fixed:

``` javascript
giphy: {
    key : "dc6zaTOxFJmzC"
}
```

### YouTube
You can find instructions for getting YouTube API Keys here: https://developers.google.com/youtube/v3/getting-started#before-you-start

``` javascript
youtube: {
    key : "vy2u1t34bo123bu41234yduv1234tb"
}
```

### SoundCloud
SoundCloud API keys can be obtained from your app profile (this requires an account): http://soundcloud.com/you/apps

``` javascript
soundcloud: {
    key : "vy2u1t34bo123bu41234yduv1234tb"
}
```

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


``` javascript
traffic: {
  key : "9kjn22lk25h0qergp34v0u9n2352437823b76823498243245",
  reload_interval : 5,
  trips : [{
    mode : "Walking",
    origin : "56 Leamington Street, Sheffield, S10 1LW",
    destination : "Claremount Cres, Sheffield, S10 2TA",
    name : "uni"
  },
  {
    mode : "Transit",
    origin : "128 24th Ave E, Seattle",
    destination : "700 Bellevue Way NE, Bellevue",
    name : "work"
  },
  {
    mode : "Driving",
    origin : "138 24th Ave E, Seattle", 
    destination : "700 Bellevue Way NE, Bellevue",
    name : "work"
  }]
}
```

If any of your trips aren't showing up it's likely because Bing Maps can't find the address you specified. Using a full postal address should fix this issue.

## Errors
Note that if you start the mirror and get a white screen you most likely have an issue with your config. Often this is caused by a missing comma somewhere within the config. Use of an online javascript linter to help find common syntax errors. 

Next Step: [Configure the Pi](configure_the_pi.md)
