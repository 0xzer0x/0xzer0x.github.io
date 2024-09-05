---
title: Tracking prayer times in tiling window managers
summary: Install and configure a prayer times module for your tiling window manager, including status bar and notifications
description: Install and configure a prayer times module for your tiling window manager, including status bar and notifications
date: 2024-09-03
ShowReadingTime: false
hideMeta: true
ShowToc: true
ShowPostNavLinks: false
tags:
  - linux
  - window manager
  - scripting
  - bash
images: imgs/blogs/statusbar-prayer-times.png
cover:
  image: imgs/blogs/statusbar-prayer-times.png
---

## Introduction

One of the key benefits of using tiling window managers is the ability to
easily extend functionality through custom Bash scripts. Embracing this
flexibility, I created a Bash script specifically designed to track prayer
times. This script integrates with various status bars and notification
daemons, offering a streamlined way to stay informed about prayer times
directly from your desktop environment.

## Quick Start

To quickly install the prayer times script, follow these steps:

1. Clone the repository:

```sh
git clone https://github.com/0xzer0x/prayer-times.git
```

2. Run the installation script:

```sh
cd prayer-times
./install.sh
```

## Scripts

### Prerequisites

Before using the script, you need to have the following dependencies installed on your system:

- `jq`
- `at`
- `yad`
- `mpv`
- `curl`
- `dunst` (for X11)
- `polybar` (for X11)
- `mako` (for Wayland)
- `waybar` (for Wayland)
- [Nerd Font](https://www.nerdfonts.com/) (recommended)

#### Ubuntu

```bash
sudo apt install jq at yad mpv curl dunst polybar mako waybar
```

#### Fedora

```bash
sudo dnf install jq at yad mpv curl dunst polybar mako waybar
```

#### Arch

```bash
sudo pacman -S jq at yad mpv curl dunst polybar mako waybar
```

### Installation

You need to copy the files from [`0xzer0x/prayer-times`](https://github.com/0xzer0x/prayer-times) to the following paths:

- `.local/bin`: `~/.local/bin`
- `.local/share/qatami_takbeer.mp3`: `~/.local/share/qatami_takbeer.mp3`
- `.config/systemd/user`: `~/.config/systemd/user`

### Configuration

To configure the [`prayer-times`](https://github.com/0xzer0x/prayer-times/blob/main/.local/bin/prayer-times) script, you'll need to set the following parameters inside the script:

- `lat`: latitude
- `long`: longitude
- `method`: calculation method
- `print_lang`: language to print prayer times schedule in (`ar`/`en`)
- `notify`: notification daemon (`mako`/`dunst`)

### Systemd Unit

To sync the prayers calendar and create the `at` jobs automatically, you can
activate one of the following Systemd services based on your preferences:

- **On boot:** `systemctl --user enable --now prayer-times.service`
- **On boot + every 8 hours:** `systemctl --user enable --now prayer-times.timer`

## Bar Module

To add the next prayer to your statusbar, you will need to add a custom module to your bar's config.

### Polybar

- Add the following to your [Polybar config](https://github.com/polybar/polybar/wiki/Configuration)
- Modify colors according to your liking (replace `#83CAFA`)

```ini
[module/prayers]
type = custom/script
exec = $HOME/.local/bin/prayer-times status
interval = 60
label = %{A:$HOME/.local/bin/prayer-times yad:}%{F#83CAFA}󱠧 %{F-} %output%%{A}
```

### Waybar

- Add the following custom module to your [Waybar config](https://github.com/Alexays/Waybar/wiki/Configuration)
- You can style the module using the class of the next prayer (e.g. `Asr`)

```json
"custom/prayers": {
  "interval": 60,
  "return-type": "json",
  "exec": "$HOME/.local/bin/prayer-times waybar",
  "on-click": "$HOME/.local/bin/prayer-times yad",
  "format": "󱠧  {}",
}
```

## Athan Notification

### Dunst

- Add the following rule to your dunstrc file (`~/.config/dunst/dunstrc`)

```ini
[play_athan]
summary = "Prayer Times"
script = "$HOME/.local/bin/toggle-athan"
```

### Mako

- Add the following criteria/rule to mako config (`~/.config/mako/config`)

```ini
[summary="Prayer Times"]
on-notify=exec $HOME/.local/bin/toggle-athan
on-button-left=exec $HOME/.local/bin/toggle-athan
```

## Prayer Times Window

- Window Title: `Prayers`
- Configure your window manager to show the Yad window in floating mode and you're all set!
- Example window rule for [Hyprland](https://hyprland.org/)

```ini
windowrulev2 = float,class:(yad)
windowrulev2 = move cursor -50% 30,title:(Prayers)
```
