+++
title = "Help Wanted Solving Our BLE Stack Problem"
date = 2019-06-13
+++

<p align="center">
<img src="COH4s8I.jpg" width="50%"/>
</p>

TL;DR: Read [this](https://github.com/jonas-schievink/rubble/issues/29#issuecomment-483387629) and open a PR to close the issue ❤️

[Jonas Schievink](https://github.com/jonas-schievink) and I have been working on a Bluetooth Low Energy stack in Rust, [Rubble](https://github.com/jonas-schievink/rubble). It is now in a state where hard-coded services can be created and used, with all lower layers of the stack functioning. 

The next step is designing and implementing both an interface for managing Services and Characteristics, as well as a system for notifications when a value is changed. This is fairly complex, with no clear or obvious solution hence the call for help.

## Constraints

We have some constraints that have made implementing the aformentioned difficult. These include hard requirements such as `no_std` (of course) and no allocating, as well as softer aims such as keeping SRAM and flash usage low (currently at 450 bytes and 20K bytes respectively). There is also the nature of microcontrollers' limited processing speed so reducing work at runtime is key, I.E when it comes to creating Attributes from Services.

## Crash course BLE

[This page](https://devzone.nordicsemi.com/nordic/short-range-guides/b/bluetooth-low-energy/posts/ble-characteristics-a-beginners-tutorial) has a good explaination, but I'll summarise.

### Attribute

The ATT protocol describes "Attributes" which are essentially the smallest unit for transferring data. Attributes have the following fields:

* Handle, uniquely identifies it on a server
* Type, 16 or 128 bit UUID corresponding to pre-defined types
* Permissions, describing who can read/write with what authorization
* Value, can be anything from heart rate in BPM to whether a switch is on or off

### Characteristic

A Characteristic is a defined type with a single logical value. A Characterstic is defined with the following Attributes:

* Declaration, with type "Characteristic Declaration" (0x2803), read only permissions and value containing the type of the value, the handle of the Value Declaration, and properties
* Value Declaration with a type, handle and value

### Service

A Service is a set of required and optional Characteristics. Some Services have been predefined by the Bluetooth SIG, but can be custom.

## Services/Characteristic Management

In the [GATT module](https://github.com/jonas-schievink/rubble/blob/8518039e7ef8db7dd2499e82e6c049c60b15b394/rubble/src/gatt/mod.rs) a GattServer just contains a single fixed Attribute. We need users of the library to be able to specify Characteristics and/or Services, and somehow turn that into a list of Attributes. This should most likely be done at compile time, and could possibly be a macro, but we have struggled to find a nice implementation.

## Notification System

Attribute values might be changed by either the device running the stack, or a connected device. The other must be notified somehow that this has happened.
For example, if the air temperature of a thermostat changes, a notification needs to be sent to the external device to display the new value. Similarly, if a user makes a request to toggle a smart switch, Rubble needs a way to run a function that actually toggles the switch.

## Hardware

Nordic has a some developer kits, and it is definitely feasible to use a nRF52 module from Aliexpress soldered to a debugger.

~~For development I would recommend the [Adafruit Bluefruit LE Friend](https://www.adafruit.com/product/2267) along with an STLink or other probe. Rubble currently uses logging over serial so the built in USB to UART is nice.~~

Edit: [nRF51 support is not ready yet](https://github.com/jonas-schievink/rubble/pull/59).
