# Development and Contributing

##### Development
 See the `dev` branch for features that are actively in development.
If you would like to contribute please follow the [contribution guidelines](https://github.com/evancohen/smart-mirror/blob/master/CONTRIBUTING.md).
To launch the mirror with a debug window attached use the following command:
```
npm start dev
```

You can keep up with development on http://waffle.io/evancohen/smart-mirror

##### Contributing
 Everybody is invited and welcome to contribute to smart-mirror. There is a lot to do... If you are not a developer perhaps you would like to help with the documentation on [docs.smart-mirror.io](http://docs.smart-mirror.io/)? If you are a developer and have a feature/capability you'd like to see, why not spent a couple of hours and help build it? 

The process is straight-forward.

 - Fork the smart mirror [git repository](https://github.com/evancohen/smart-mirror).
 - Write the code for your feature/capability.
 - Create a Pull Request against the [**dev**](https://github.com/evancohen/smart-mirror/tree/dev) branch of the smart mirror.

### Project Structure
 The smart mirror is an [Electron](electron.atom.io) app, which means it leverages Chromium, Node, and the V8 JavaScript engine to host and render the mirror.
 
#### [config.example.js](https://github.com/evancohen/smart-mirror/blob/master/config.example.js)
  While not ever actually included in the mirror, `config.example.js` serves as a config template for users to base their own `config.js` file on. In general these values are optional (but there is some inconsistency in the way this works today).

#### [js/](https://github.com/evancohen/smart-mirror/tree/master/js)
 The `js` directory contains the core of the smart-mirror: 
 - `app.js` manually bootstraps Angular 
 - `controller.js` controls all the data binding, voice command registration, and service injection for the mirror.

#### [js/services/](https://github.com/evancohen/smart-mirror/tree/master/js/services)
 The `services` directory is home to all the service integration logic for the mirror. Each file in this directory does the heavy lifting for it's respective service and serves as an interface between the mirror and that service.
 
 Services adhere to [Promise-Based Archetecture](http://blog.rangle.io/the-art-of-promise-based-architecture/) and should avoid containing long-running functions. 

#### [locales/](https://github.com/evancohen/smart-mirror/tree/master/locales)
 Within this directory you will find all the `JSON` localization files for the mirror. The mirror uses [i18n](https://angular-translate.github.io/) to `$translate` strings rendered in the mirror (examples of this in `index.html` and `config.js`).
 
 When making changes to these files make sure that you add string keys to all localization files, not just to the one that you speek.
 
 #### [scripts/](https://github.com/evancohen/smart-mirror/tree/master/scripts)
  Contains various help scripts. There aren't a ton today and they will expand over time.
  
  ### Tips and tricks
   The dev console is your friend! You can set breakpoints, log messages, and inspect the DOM - just like you would in a regular webdev console.

#### Speech Simulation
   Since speech query limitations have becoming a limeting factor of development I've created a shim for Annyang to "simulate" speech to test the mirror. In the dev console try some of these examples:
``` javascript
// Play YouTube video
annyang.simulate("show me how to tie a bowtie");

// Play a song on SoundCloud
annyang.simulate("SoundCloud play Kero One so seductive");

// Display a map
annyang.simulate("show me a map of Seattle Washington");
```

#### Dev Environment
 I typically wouldn't recommend developing directly on the Pi (unless you are trying to debug a Pi specific issue, in which case, I'm sorry. It's not the fastest thing in the world. 
 
 The mirror is compatible with Windows and OSX, and developing there will be much nicer. You can plug your mirror into your computer and use it as a second (or third, you lucky duck) monitor. There's some logic in `main.js` that will automatically put the electron app on to your secondary monitor.
