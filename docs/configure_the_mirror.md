# Configure the smart-mirror

The smart-mirror relies on a configuration file to determine what data to display. 

You'll need to create a `config.js` file in the root of your smart-mirror directory. Also in this directory is a configuration template called `config.example.js`. Copy the template and save it as `config.js`.
```
cp config.example.js config.js
```

Then fill out `config.js`, which should end up looking something like this:
``` javascript
var config = {
    language : "en", 
    layout: "main",
    greeting : ["Hi, sexy!", "Hey There!", "Looking Awesome!"], 
    forcast : {
        key : "a6s5dg39j78qj38sjs91je9djadfa1e", 
        units : "auto" 
    },
    hue : {
        ip : "192.168.1.99", 
        uername : "as9234ho0dfhoq01f2as3yh4m0", 
        group : "0" 
    },
    calendar: {
      icals : ["https://calendar.google.com/calendar/ical/SOMESTUFF/basic.ics",
"https://outlook.office365.com/owa/calendar/SOMESTUFF/reachcalendar.ics"],
      maxResults: 9, 
      maxDays: 365 
    },
    giphy: {
      key : "a6s5dg39j78qj38sjs91je9djadfa1e" 
    },
    traffic: {
      key : "a6s5dg39j78qj38sjs91je9djadfa1e",
      mode : "Driving",
      origin : "350 5th Ave, New York, NY 10118",
      destination : "1 Dr Carlton B Goodlett Pl, San Francisco, CA 94102",
      name : "work",
      reload_interval : 5
    }
};
```
Note that if you start the mirror and get a white screen you most likeley have an issue with your config.

Next Step: [Configure the Pi](configure_the_pi.md)