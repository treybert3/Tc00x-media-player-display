 
# Awtrix TC00x Media Control & Display Blueprint

A Home Assistant blueprint using MQTT to control and display media player volume on an Ulanzi TC001 or TC002 pixel display running **Awtrix Light / Awtrix NG**.

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

## Prerequisites

1. An **Ulanzi TC001 or TC002** running Awtrix Light / Awtrix NG firmware.
2. An active **MQTT Broker** (e.g., Mosquitto) configured in Home Assistant and connected to your display.
3. A configured `media_player` entity in Home Assistant (e.g., Sonos, Apple TV, AV Receiver).

---

## Awtrix NG Setup Instructions

<!-- TODO: Add specific Awtrix NG hardware & software setup steps below -->

### Setting up the TC001
*Add setup instructions for TC001 here...*

### Setting up the TC002
*Add setup instructions for TC002 here...*

---

## Installation

### Method 1: Automatic Import (Recommended)

Click the **Import to Home Assistant** badge above, or paste the link below into Home Assistant (**Settings > Automations & Scenes > Blueprints > Import Blueprint**):

```text
[https://github.com/treybert3/Tc00x-media-player-display/blob/main/Awtrix_tc00x_media_control.yaml](https://github.com/treybert3/Tc00x-media-player-display/blob/main/Awtrix_tc00x_media_control.yaml)
