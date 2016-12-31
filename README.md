<h1 align="center">Smart Mirror</h1>

<p align="center">
<a href="https://discord.gg/JDnHaZH"><img src="https://discordapp.com/api/guilds/258802311298547713/widget.png" alt="Discord Chat"/></a>
<a href="https://waffle.io/evancohen/smart-mirror"><img src="https://img.shields.io/waffle/label/evancohen/smart-mirror/in%20progress.svg" alt="Stories in progress" /></a>
<a href='https://dependencyci.com/github/evancohen/smart-mirror'><img src='https://dependencyci.com/github/evancohen/smart-mirror/badge' alt='Dependency Status'/></a>
</p>
<p align="center">
A voice controlled life automation hub, most commonly powered by the Raspberry Pi.
</p>

# Introduction

This is the official documentation for the [smart-mirror](https://github.com/evancohen/smart-mirror). If you are reading this on [docs.smart-mirror.io](http://docs.smart-mirror.io), great! If not you should head on over.

The smart-mirror was inspired by [HomeMirror](https://github.com/HannahMitt/HomeMirror) and Michael Teeuw's [Magic Mirror](http://michaelteeuw.nl/tagged/magicmirror). It was originally created in a weekend and is now maintained by a growing community of contributors and enthusiasts. 

Smart-mirror is voice controlled, integrates with a growing number of services, and can control your smart devices :)

##### Video Demo: [See it in action](https://youtu.be/PDIbhV8Nvq8)
{% youtube %}
https://www.youtube.com/watch?v=PDIbhV8Nvq8
{% endyoutube %}
> Note: The current video demonstrations do not display the mirror in its current state. Such as keyword spotting and remote configuration.

Starting from scratch? No problem. Head on over to the [Hardware](docs/hardware.md) section to get started.

If you encounter problems along the way check out the [Troubleshooting](docs/troubleshooting.md) section or join us in the [discord chat](https://discord.gg/JDnHaZH).

Please file any issues or bugs [on GitHub](https://github.com/evancohen/smart-mirror/issues/new).


## About this documentation

This documentation is a constant work in progress. It is updated as we find issues and as we add new features. Who is the "we"? We are a community of people contributing, supporting, and improving this project. We are working to make the documentation as helpful, clear, and accurate as possible. 

Issues and concerns with the documentation?
Please file an issue [on GitHub](https://github.com/evancohen/smart-mirror/issues/new). Commenting in line can cause readability issues for others. It is also difficult for anyone other than Evan Cohen to address or remove after resolving the documentation.

> #### This project is a step by step process. For successful installation and configuration you must follow it step by step. If you skip a step that seems insignificant it can cause a catastrophic error down the line. Often when troubleshooting in the [gitter chat](https://gitter.im/evancohen/smart-mirror) we determine that a step was missed. 
![](docs/mirrorBoom.jpg)
> #### Having said that we don't mind, nearly everyone on [discord chat](https://discord.gg/JDnHaZH) that has a working install has skipped a step and gone back and fixed it. We're here to help. Following the documentation step by step will greatly reduce your level of frustration while getting started on this project.


### Supported Platforms
The smart-mirror is fully compatible with the following operating systems. Note that a small number of features require GPIO, devices without this will not be able to take advantage of these features.

- ![](docs/raspbian.png) Raspbian
  - Pi 2
  - Pi 3
- ![](docs/linux.png) Linux (Most major distributions)
- ![](docs/mac.png) OS X >= 10.8

### Partially supported Platforms
The smart-mirror is partially compatible with the following operating systems
- ![](docs/windows.png) Windows 7 / Server 2008 R2 or higher
  - Keyword Spotter is not supported. See [snowboy#31](https://github.com/Kitt-AI/snowboy/issues/31).
- ![](docs/cordova.png) iOS and Android (Experimental!)
  - See the `cordova` branch for details