# Development and Contributing
># `NOTE: This is a work in progress.`


You can keep up with development on http://waffle.io/evancohen/smart-mirror

## Contributing
 Everybody is invited and welcome to contribute to the smart mirror. There is a lot to do... If you are not a developer perhaps you would like to:
 - **Help with the documentation** on [docs.smart-mirror.io](http://docs.smart-mirror.io/), 
 - **Localize the smart mirror** in a new language language (or improve an existing one)
 - **Helping others** on [Discord](https://discord.gg/EMb4ynW).
 
If you are a developer and have a feature/capability you'd like to see, why not spent a couple of hours and help build it? 

The process is straight-forward.

 - Fork the smart mirror [git repository](https://github.com/evancohen/smart-mirror).
 - Write the code for your feature/capability.
 - Create a Pull Request against the [**dev**](https://github.com/evancohen/smart-mirror/tree/dev) branch of the smart mirror.

## Development
 See the `dev` branch for features that are actively in development.
If you would like to contribute please follow the [contribution guidelines](https://github.com/evancohen/smart-mirror/blob/master/CONTRIBUTING.md).
To launch the mirror with a debug window attached use the following command:
```
npm start dev
```
### Project Structure
 The smart mirror is an [Electron](electron.atom.io) app, which means it leverages Chromium, Node, and the V8 JavaScript engine to host and render the mirror.

#### [app/](https://github.com/evancohen/smart-mirror/tree/master/app)
 The app directory contains the core of the smart-mirror: 
 - **`js/`** core js of the smart mirror (bootstrapping angular, etc) 
 - **`css/`** all of the smart mirror styles
 - **`locales/`** all of the localized speech commands (more on this later)
 - **`fonts/`** nobody knows what this folder does, but it's somehow necessary ;)
 
#### [plugins/](https://github.com/evancohen/smart-mirror/tree/master/plugins)
The plugins directory contains all of the plugins included in the smart mirror. A plugin consists of an optional combination of the following:
- **`config.schema.json`** defines the configuration schema for your plugin. You can look at example schema and test your own at https://smart-mirror.io/playground/
- **`index.html`** the html partial for your plugin. This must be added to the main [index.html](https://github.com/evancohen/smart-mirror/blob/master/index.html) to determine where it will be rendered.
- **`controller.js`** All of the angular controller logic (data binding) for your plugin. This must be manually included in a script tag in the main [index.html](https://github.com/evancohen/smart-mirror/blob/master/index.html). It is acceptable to write *Node* here.
- **`service.js`** should your plugin need an angular service you can manually included in a script tag in the main [index.html](https://github.com/evancohen/smart-mirror/blob/master/index.html).

#### [remote/](https://github.com/evancohen/smart-mirror/tree/master/remote)
The remote directory contains the code that powers the client configuration page(s). The "server" side code can be found in [`remote.js`](https://github.com/evancohen/smart-mirror/blob/master/remote.js).

#### [app/locales/](https://github.com/evancohen/smart-mirror/tree/master/locales)
 Within this directory you will find all the `JSON` localization files for the mirror. The mirror uses [i18n](https://angular-translate.github.io/) to `$translate` strings rendered in the mirror (examples of this in `index.html` and `config.js`).
 
 When making changes to these files make sure that you add string keys to all localization files, not just to the one that you speak.
 
 #### [scripts/](https://github.com/evancohen/smart-mirror/tree/master/scripts)
  Contains various help scripts. There aren't a ton today and they will expand over time.
  
  ### Tips and tricks
   The dev console is your friend! You can set breakpoints, log messages, and inspect the DOM - just like you would in a regular webdev console.

#### Speech Simulation
   Since speech query limitations have becoming a limeting factor of development I've created a shim for Annyang to "simulate" speech to test the mirror. In the dev console try some of these examples:
``` javascript
// Play YouTube video
annyang.trigger("show me how to tie a bowtie");

// Play a song on SoundCloud
annyang.trigger("SoundCloud play Kero One so seductive");

// Display a map
annyang.trigger("show me a map of Seattle Washington");
```

#### Dev Environment
 I typically wouldn't recommend developing directly on the Pi (unless you are trying to debug a Pi specific issue, in which case, I'm sorry. It's not the fastest thing in the world. 
 
 The mirror is compatible with Windows and OSX, and developing there will be much nicer. You can plug your mirror into your computer and use it as a second (or third, you lucky duck) monitor. There's some logic in `main.js` that will automatically put the electron app on to your secondary monitor.
