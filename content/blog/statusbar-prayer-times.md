---
title: Tracking prayer times in tiling window managers
summary: Install and configure go-pray to show prayer times in your status bar and get notified at prayer time
description: Install and configure go-pray to show prayer times in your status bar and get notified at prayer time
date: 2024-09-03
lastmod: 2026-11-14
ShowReadingTime: false
hideMeta: true
ShowToc: true
ShowPostNavLinks: false
tags:
  - linux
  - window manager
  - go
images: imgs/blogs/statusbar-prayer-times.png
cover:
  image: imgs/blogs/statusbar-prayer-times.png
---

## Introduction

One of the key benefits of using tiling window managers is the ability to
easily extend them with small command line tools. [go-pray](/projects/go-pray/)
is a prayer times CLI that fits right into this workflow: it prints the next
prayer for your status bar, shows the prayer calendar for any date, and runs as
a daemon that sends a desktop notification and plays the athan at prayer time.

{{< info >}}
This post previously used the [`prayer-times`](https://github.com/0xzer0x/prayer-times)
Bash script. go-pray replaces it with a single binary, so it no longer needs
`at`, `yad`, `mpv`, `curl`, or a Systemd unit.
{{< /info >}}

## Installation

Install the latest release with a single command:

```sh
curl -fsSLo - https://github.com/0xzer0x/go-pray/raw/refs/heads/main/install.sh | bash
```

The script installs the right package for your distro:

| Distro              | Install method  |
| ------------------- | --------------- |
| **Debian / Ubuntu** | `.deb` package  |
| **Fedora / RHEL**   | `.rpm` package  |
| **Alpine**          | `.apk` package  |
| **Arch Linux**      | AUR             |
| **Others**          | Generic tarball |

On other distros, it falls back to the generic tarball and installs `go-pray` to `./bin`.
Move the binary to a directory in your `PATH`.

To install a specific version, set `INSTALL_VERSION` (not supported on Arch Linux):

```sh
curl -sLo - https://github.com/0xzer0x/go-pray/raw/refs/heads/main/install.sh \
| env INSTALL_VERSION=0.1.3 bash
```

### Nix

If you use [Nix](https://nixos.org), add the package from the project's flake to your user profile:

```sh
nix profile add github:0xzer0x/go-pray
```

For NixOS and the Home Manager module, see the
[installation wiki page](https://github.com/0xzer0x/go-pray/wiki/Installation#nix).

## Configuration

go-pray reads a `config.yml` file from the first of these locations that exists:

1. `$XDG_CONFIG_HOME/go-pray`
2. `$HOME/.config/go-pray`
3. `$HOME/.go-pray`

You can also pass a different file with `--config`. A minimal configuration needs
your location and a calculation method:

```yaml
# ~/.config/go-pray/config.yml
language: en
timezone: Africa/Cairo

location:
  lat: 30.001780
  long: 31.290419

calculation:
  # EGYPT, MWL, KARACHI, UAQ, DUBAI, ISNA, KUWAIT, QATAR, SINGAPORE, UOIF, or OTHER
  method: EGYPT

# Athan to play at prayer time (required for the daemon)
adhan: $HOME/.local/share/qatami_takbeer.mp3

notification:
  icon: dialog-information
  title: Prayer Times
  body: It is time for {{ .CalendarName }} prayer!
```

- Get your coordinates from [Map Coordinates](https://www.mapcoordinates.net/en).
- `timezone` takes an [IANA time zone](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones#List), and defaults to your local time zone.
- Set `language: ar` for Arabic output. The notification text can be Arabic too:

```yaml
language: ar
notification:
  title: "مواقيت الصلاة"
  body: "حان الآن وقت صلاة {{ .CalendarName }}"
```

`CalendarName` is the current prayer's name, and says Jumuaa instead of Dhuhr on
Fridays. For custom calculation parameters and time adjustments, see the
[configuration wiki page](https://github.com/0xzer0x/go-pray/wiki/Configuration).

## Usage

Show the next prayer:

```sh
go-pray next
```

Show when a specific prayer comes next (`fajr`, `sunrise`, `dhuhr`, `asr`, `maghrib`, or `isha`):

```sh
go-pray next fajr
```

Show the prayer calendar for today, or for any date as `YYYY-MM-DD`,
`@yesterday`, or `@tomorrow`:

```sh
go-pray calendar
go-pray calendar @tomorrow 2026-12-01
```

Use `--format` to choose between `short` (default), `table`, and `json` output.

## Notifications

`go-pray daemon` sends a desktop notification and plays the athan at each prayer
time. Start it from your window manager's autostart. For example, in your
[Hyprland](https://wiki.hyprland.org/Configuring/) configuration:

```ini
exec-once = go-pray daemon
```

## Status Bar

### Waybar

Dependencies:

- `jq`
- [Nerd Font](https://www.nerdfonts.com/)

Add the following script as `scripts/go-pray` in your
[Waybar configuration directory](https://github.com/Alexays/Waybar/wiki/Configuration#config-file),
and make it executable:

```bash
#!/usr/bin/env bash
set -euo pipefail

# WARN: make sure go-pray is in your PATH
_text="$(go-pray next)"
_calendar="$(go-pray calendar)"
_class="$(cut -d' ' -f1 <<<"${_text}")"

jq \
  --null-input \
  --unbuffered \
  --compact-output \
  --arg class "${_class}" \
  --arg text "${_text}" \
  --arg calendar "${_calendar}" \
  '{ "text": "\($text)", "tooltip": "\($calendar)", "class": "\($class)" }'
```

Then add the module to your Waybar configuration:

```json
"custom/go-pray": {
  "interval": 60,
  "return-type": "json",
  "exec": "$HOME/.config/waybar/scripts/go-pray",
  "format": "󱠧  {}",
}
```

The module shows the next prayer, and its tooltip shows today's calendar. You can
style it in your Waybar CSS using the class of the next prayer (e.g. `Asr`).
