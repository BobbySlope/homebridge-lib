# homebridge-lib
[![npm](https://img.shields.io/npm/dt/homebridge-lib.svg)](https://www.npmjs.com/package/homebridge-lib) [![npm](https://img.shields.io/npm/v/homebridge-lib.svg)](https://www.npmjs.com/package/homebridge-lib)
[![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com)

## Utility Library for Homebridge Plugins
Copyright © 2017,2018 Erik Baauw. All rights reserved.

While developing a number of [Homebridge](https://github.com/nfarina/homebridge) plugins, I find myself duplicating a lot of code.  The idea behind this utility library is to ease developing and maintaining Homebridge plugins by separating this generic code, dealing with [HomeKit](http://www.apple.com/ios/home/) and Homebridge, from the specific code, dealing with the actual devices being exposed to HomeKit.

The `homebridge-lib` library provides the following functionality:
- Saving and restoring accessories from persistent storage between Homebridge sessions (using the homebridge v2 dynamic platform model);
- History for [Eve](https://www.evehome.com/en/eve-app);
- Universal Plug & Play (UPnP) device discovery;
- Setting up a heartbeat for device polling;
- Logging and error handling;
- Defining custom HomeKit services and characteristics;
- Checking the NodeJS and Homebridge versions used;
- Checking the latest plugin version published to the NPM registry;
- Utility functions for: JSON formatting, calling a REST API, parsing `config.json`.

Technically, the `homebridge-lib` library is based on the following:
- Using asynchronous functions rather than callback functions;
- Using javascript classes rather than prototypes.  An actual plugin extends the classes provided by `homebridge-lib`;
- Using events.  In fact all `homebridge-lib` classes extend `EventEmitter`;

The `homebridge-lib` library provides a number of abstract superclasses, that act as delegate for HomeKit accessories, services, and characteristics.  A Homebridge plugin based on `homebridge-lib` extends these classes, providing the device-specific logic.

See the [Wiki](https://github.com/ebaauw/homebridge-lib/wiki) for more information.  See [`homebridge-ws`](https://github.com/ebaauw/homebridge-ws) as an example plugin based on `homebridge-lib`.

## Installation
This library is _not_ a Homebridge plugin and should not be installed manually.  Instead, Homebridge plugins using this library should list it as a dependency in their `package.json`.  This way, `npm` installs `homebridge-lib` automatically when installing the actual plugin.

## Credits
The logic for handling [Eve](https://www.evehome.com/en/eve-app) history was copied from Simone Tisa's [`fakegato-history`](https://github.com/simont77/fakegato-history) repository, copyright © 2017 simont77.
