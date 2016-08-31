# Introduction

This is the official documentation for the [smart-mirror](https://github.com/evancohen/smart-mirror). If you are reading this on [docs.smart-mirror.io](http://docs.smart-mirror.io), great! If not you should head on over.

Smart-mirror was inspired by [HomeMirror](https://github.com/HannahMitt/HomeMirror) and Michael Teeuw's [Magic Mirror](http://michaelteeuw.nl/tagged/magicmirror). It was originally created in a weekend and is now maintained by a growing community of contributors and enthusiasts. 

Smart-mirror is voice controlled, integrates with a growing number of services, and can control your smart devices :)

##### Video Demo: [See it in action](https://youtu.be/PDIbhV8Nvq8)
{% youtube %}
https://www.youtube.com/watch?v=PDIbhV8Nvq8
{% endyoutube %}

Starting from scratch? No problem. Head on over to the [Hardware](docs/hardware.md) section to get started.

If you encounter problems along the way check out the [Troubleshooting](docs/troubleshooting.md) section or join us in the [gitter chat](https://gitter.im/evancohen/smart-mirror).

Please file any issues or bugs [on GitHub](https://github.com/evancohen/smart-mirror/issues/new).

### Supported Platforms

Smart-mirror is compatible and currently all features are supported with the following operating systems:

- ![](docs/raspbian.png) Raspbian
  - Pi 2
  - Pi 3

### Unsupported Platforms

Smart-mirror is either partially compatible or some features are not supported with the following operating systems:

- ![](docs/linux.png) Linux (Most major distributions)
  - Features requiring RPiGPIO is not available 
- ![](docs/windows.png) Windows 7 / Server 2008 R2 or higher
  - Keyword Spotter is not supported. Snowboy has not released a pre-compiled binary [Snowboy#31](https://github.com/Kitt-AI/snowboy/issues/31)
  - Features requiring RPiGPIO is not available
- ![](docs/windows.png) Windows 10 IoT Core
  - Windows 10 IoT has no gui. Therefore, is not compatible with this project.
- ![](docs/mac.png) OS X >= 10.8
  - Most components are compatible however recieving support is limited to users available on gitter at given time.
  - Features requiring RPiGPIO is not available
- ![](docs/cordova.png) iOS and Android (Experimental!)
  - See the `cordova` branch for details
  - Features requiring RPiGPIO is not available
