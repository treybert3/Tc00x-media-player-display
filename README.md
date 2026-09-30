 
# Awtrix TC00x Media Control & Display Blueprint

A Home Assistant blueprint using MQTT to control and display media player volume on an Ulanzi TC001 or TC002 pixel display running **Awtrix NG**.

[![Open your Home Assistant instance and show the blueprint import dialog with the repository URL pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Ftreybert3%2FTc00x-media-player-display%2Fblob%2Fmain%2FAwtrix_tc00x_media_control.yaml)

---

## Purpose

Many modern soundbars (such as Sonos) lack a built-in numerical volume display. Additionally, when controlling audio through older TVs or external remotes, the screen often only shows an indicator that the volume changed—without displaying the actual numeric level.

This blueprint bridges that gap by using an Ulanzi TC001 or TC002 running Awtrix NG as an external volume indicator and control interface.

---

## Features

- **TC002:** Knob-based volume control with press-to-mute/unmute.
- **TC001:** Button-based volume control (Left/Right) with select-to-mute.
- **Universal Volume Sync:** Displays the volume whenever it changes from **any source**—whether adjusted physically via the clock, through a mobile app, or via an external remote control.
- **Customizable Interface:** Supports custom text colors (`#RRGGBB`), notification durations, and custom icon IDs.

---


## How it works

It's very straight forward. The TC001/2 devices are configured to generate MQTT messages when a button is pressed. Homeassistant is then watching for those messages and sends the commands to increase/decrease volume to the chosen media player. Homeassistant is also watching for when the volume changes on the media player and sends a MQTT notification message to the TC001/2. 

This allows for the volume change to get reflected on the display regardless of the source. For example, I can change the volume from my Sonos app and I will see the results on the display, as well as being able to change it directly from the display.

---
## Prerequisites

1. An **Ulanzi TC001 or TC002** running Awtrix NG firmware.
2. An active **MQTT Broker** (e.g., Mosquitto) configured in Home Assistant and connected to your display.
3. A configured `media_player` entity in Home Assistant (e.g., Sonos, Apple TV, AV Receiver).

---
### Setting up the TC001
Follow blueforcer's instructions here
[https://blueforcer.github.io/awtrix-ng/](https://blueforcer.github.io/awtrix-ng/getting-started/flashing/)

Once awtrix_ng is installed and connected to your wifi, you'll want to do the following:
1. Connect to the device's IP via any web browser.
2. Connect to mqtt under the system tab
3. Take note of your chosen prefix topic (ie Awtrix01), you'll need it later
4. Find an icon from LaMetric: Web for the volume notification, load it into awtrix in the icons tab. Note the icon# as you'll need it later.

5. If you plan on using the 2 buttons to control the volume, you'll need to disable the buttons from switching apps. Display -> App Rotation -> Block Buttons

6. Proceed to the blueprint setup

---


### Setting up the TC002
Awtrix_ng doesn't natively support the TC002, but because people are awesome, someone has made an unofficial port. 
[https://github.com/sanderdw/awtrix-ng-tc002
](https://github.com/sanderdw/awtrix-ng-tc002)

1. Get the TC002 connected to your wifi. I would recommend connecting to its default wifi and going to the IP address listed on the display so you don't have to install any software. I personally tried using the Ulanzi Studio app at first but it requires bluetooth to start the process, which my desktop doesn't have.
2. Once the TC002 is on your network, follow the instructions in the 'Install' section [https://github.com/sanderdw/awtrix-ng-tc002
](https://github.com/sanderdw/awtrix-ng-tc002). It really does come down to running a single command but watch the pre-reqs listed.
3. Your TC002 should now be running awtrix_ng.
4. Connect to the device's IP via any web browser.
5. Connect to MQTT and take note of the chosen topic prefix
6. In the Icon's tab, you'll want to pick out an icon for the volume change and mute notifications. Go to Add and either upload a gif, find one in the icon in the hub, or make your own. Keep track of the name of the icons (the actual name, not the icon#)

7. If you plan on using the knob for volume, you'll need to disable the buttons from switching apps. Display -> App Rotation -> Block Buttons

8. Proceed to the blueprint setup

---

## Homeassistant Blueprint Installation

### Automatic Import (Recommended)

Click the **Import to Home Assistant** badge above, or paste the link below into Home Assistant (**Settings > Automations & Scenes > Blueprints > Import Blueprint**):

```text
[https://github.com/treybert3/Tc00x-media-player-display/blob/main/Awtrix_tc00x_media_control.yaml](https://github.com/treybert3/Tc00x-media-player-display/blob/main/Awtrix_tc00x_media_control.yaml)
```

### Adding the automation

1. In homeassistant after the blueprint has been imported, go to Settings -> Automations & Scenes -> Create Automation -> 'Awtrix Control & Media Player Sync (TC001 / TC002)
2. Device Model: select if you're using the TC001 or TC002
3. MQTT Prefix: the mqtt prefix you chose when you configured awtrix. Note this is case sensitive
4. Media Player: select the media player entity already connected in your HA system
5. Enable Volume Control Event: 

