# ESP32NotificationsLib
Easy-to-use Arduino library for interfacing an ESP 32 with Bluetooth LE mobile device notifications.

This library is designed to follow the standard Arduino library style, and be as easy to use and clear as possible for non-programmers (i.e. no lambda functions, threads, new C++ language features, etc.)

Note that this is a work in progress and is incomplete (but should work).

## Features

    * Easily start re-advertising the ESP 32 device if BLE connection is lost.
    * Apple ANCS notification support, with advanced message details.


## Installation

Put the unzipped library code into your ~/arduino/libraries/ folder, under a ESP32NotificationsLib subfolder:

Or use git:
 ```
 cd ~/arduino/libraries/
 git clone git@github.com:Smartphone-Companions/ESP32NotificationsLib.git
 ```

Then you should see the examples and be able to include the library in your projects with:

```
 #include "esp32notifications.h"
```
 
## Usage

This works like a standard Arduino library. Here's a minimal example:

```
// Create an interface to the BLE notification library at the top of your sketch
BLENotifications notifications;

// Start looking for a device connection
notifications.begin("BLEConnection device name");

// Setup a callback for when a notification arrives
void onNotificationArrived(const Notification * notification) {
    Serial.println(notification->title.c_str());
}

// Register the callback to be informed when a notification arrives
notifications.setConnectionStateChangedCallback(onBLEStateChanged);
notifications.setNotificationCallback(onNotificationArrived);
```

See the ble_connection example for a more fully-featured example.

To see a real-world project, https://github.com/jhud/hackwatch uses this library.


## History / Acknowledgements

Based on the work of CarWatch, Hackwatch, and S-March. This project was created to hide the complicated BLE notification internals behind a standard, easy-to-use Arduino library.
