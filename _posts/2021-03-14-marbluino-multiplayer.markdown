---
layout: post
title: 'Marbluino: Multiplayer'
date: '2021-03-14 14:42:00 +0200'
author: jablan
lang: en
tags: marbluino esp8266 arduino
---

This is a second article in Marbluino series and discusses its multiplayer feature.

## Idea

Expanding on [original Marbluino](https://github.com/jablan/marbluino) game, I wanted to play a bit with WiFi features of ESP8266, and try making a multiplayer game out of Marbluino. The logical concept is, that each player controls a marble of their own, and they try to reach the flags faster than all the others, collecting points. At the end (either when all the players die, or when they reach the final level) the game would display the list of players ordered by their collected points. Sounds simple!

## The protocol

Traditional approach would involve every device registering to the WiFi access point, which is a bit problematic knowing the devices don't have any familiar input mechanism. This means that the registration would have to proceed similar to registering smart-home appliances, such as light bulbs and power switches. Once registered, the devices would have to communicate probably using some multicast protocol, such as UDP. Although feasible and relatively straightforward, I looked for something simpler, and found something called ESP-Now.

## ESP-Now

[ESP-Now](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/api-reference/network/esp_now.html) is a proprietary network protocol supported by ESP8266 and ESP32 devices, which does not need an AP to work. It is simple and lightweight way to send packets to other nodes knowing their MAC addresses (peer-to-peer), but it also supports broadcasting, when using `FF:FF:FF:FF:FF:FF` as a peer address. The protocol is not super popular, and there are not that many different examples around, but it seems just perfect for Marbluino: peers can communicate with as little preparation as possible. We are not interested in encryption, and we don't care much if the peer has received the packet or not.

Following some examples I found online, I created a [small example](https://github.com/jablan/espnow_pingpong) of master/slave setup, where all nodes both receive and send packages. ESP-Now limits package size to 250 bytes, but that should be plenty enough for Marbluino.

## Architecture

Unlike in a single-player setup, where a single device keeps track of the game state and makes decision about important events (such as level ups and lost lives), in a multiplayer setup, there needs to be an authority, so that there are no conflicting facts. Therefore, one device (typically the one started first) takes the role of a *master*, and those important decisions happen only there. These decisions are then broadcasted, listened to and acted upon on other nodes (slaves).

On the other hand, every slave informs every other node (regardless whether master or slave) about its own movement, again using broadcasting. This message happens on each movement cycle (current setup is 20 times per second).

When a new device is started, it publishes "hello" message, and it's the master's duty to acknowledge it, add the new device to the list, and broadcast the new list. That's how everyone else is informed about the new player.

![Peer-to-peer]({{ site_url }}/images/marbluino.png "Master and two slaves")


## Challenges

It turns out that multiplayer programming is *hard* :). My assesment is, that the complexity of the program increased roughly ten-fold with the introduction of multiplayer feature. There are many traps and not-so-edge cases which need to be covered.

For example, what happens if a device leaves? How do other device notice and acknowledge that? What happens if the device which has left was the master? Who takes over the master role and how? How to enable having multiple games in the same room?

## Conclusion

 As the code grew, I decided to move the development from Arduino IDE to a proper code editor, so it was replaced by [VS Code](https://code.visualstudio.com/) with [PlatformIO](https://platformio.org/) extension.

 I plan to continue the development and occasionally improve/add features to Marbluino. Feel free to [browse the code](https://github.com/jablan/marbluino_now), make your own device and play the game, open issues and contribute in the development.