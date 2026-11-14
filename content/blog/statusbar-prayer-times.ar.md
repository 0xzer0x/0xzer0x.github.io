---
title: تتبع أوقات الصلاة في مديري النوافذ
summary: تثبيت وتهيئة go-pray لعرض مواقيت الصلاة في شريط الحالة وتلقي الإشعارات عند دخول وقت الصلاة
description: تثبيت وتهيئة go-pray لعرض مواقيت الصلاة في شريط الحالة وتلقي الإشعارات عند دخول وقت الصلاة
date: 2024-09-03
lastmod: 2026-11-14
ShowReadingTime: false
hideMeta: true
ShowToc: true
ShowPostNavLinks: false
tags:
  - لينكس
  - مدير النوافذ
  - جو
images: imgs/blogs/statusbar-prayer-times.png
cover:
  image: imgs/blogs/statusbar-prayer-times.png
---

## مقدمة

أحد الفوائد الرئيسية لاستخدام مديري النوافذ هي القدرة على إضافة الوظائف بسهولة
عبر أدوات سطر الأوامر الصغيرة. [go-pray](/ar/projects/go-pray/) أداة سطر أوامر
لمواقيت الصلاة تناسب هذا الأسلوب: فهي تعرض الصلاة القادمة في شريط الحالة، وتعرض
تقويم الصلاة لأي تاريخ، وتعمل كخدمة في الخلفية ترسل إشعارًا وتشغّل الأذان عند دخول
وقت الصلاة.

{{< info >}}
كانت هذه التدوينة تستخدم سابقًا سكريبت باش [`prayer-times`](https://github.com/0xzer0x/prayer-times).
يحل go-pray محله كملف تنفيذي واحد، فلم يعد يحتاج إلى `at` أو `yad` أو `mpv` أو `curl`
أو وحدة Systemd.
{{< /info >}}

## التثبيت

ثبّت أحدث إصدار بأمر واحد:

```sh
curl -fsSLo - https://github.com/0xzer0x/go-pray/raw/refs/heads/main/install.sh | bash
```

يثبّت السكريبت الحزمة المناسبة لتوزيعتك:

| التوزيعة            | طريقة التثبيت |
| ------------------- | ------------- |
| **Debian / Ubuntu** | حزمة `.deb`   |
| **Fedora / RHEL**   | حزمة `.rpm`   |
| **Alpine**          | حزمة `.apk`   |
| **Arch Linux**      | AUR           |
| **غير ذلك**         | أرشيف عام     |

في التوزيعات الأخرى، يلجأ السكريبت إلى الأرشيف العام ويثبّت `go-pray` في `./bin`.
انقل الملف التنفيذي إلى مجلد ضمن `PATH`.

لتثبيت إصدار محدد، اضبط `INSTALL_VERSION` (غير مدعوم في Arch Linux):

```sh
curl -sLo - https://github.com/0xzer0x/go-pray/raw/refs/heads/main/install.sh \
| env INSTALL_VERSION=0.1.3 bash
```

### Nix

إذا كنت تستخدم [Nix](https://nixos.org)، أضف الحزمة من Flake المشروع إلى ملفك الشخصي:

```sh
nix profile add github:0xzer0x/go-pray
```

لإعداد NixOS ووحدة Home Manager، راجع
[صفحة التثبيت في الويكي](https://github.com/0xzer0x/go-pray/wiki/Installation#nix).

## التهيئة

يقرأ go-pray ملف `config.yml` من أول مسار موجود من المسارات التالية:

1. `$XDG_CONFIG_HOME/go-pray`
2. `$HOME/.config/go-pray`
3. `$HOME/.go-pray`

ويمكنك تحديد ملف آخر باستخدام `--config`. تحتاج التهيئة الأساسية إلى موقعك وطريقة
الحساب:

```yaml
# ~/.config/go-pray/config.yml
language: ar
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
  title: "مواقيت الصلاة"
  body: "حان الآن وقت صلاة {{ .CalendarName }}"
```

- احصل على إحداثياتك من [Map Coordinates](https://www.mapcoordinates.net/en).
- يقبل `timezone` [منطقة زمنية بصيغة IANA](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones#List)، والقيمة الافتراضية هي منطقتك الزمنية المحلية.
- `language` تحدد لغة المخرجات: `ar` للعربية أو `en` للإنجليزية (الافتراضية).

`CalendarName` هو اسم الصلاة الحالية، ويصبح الجمعة بدلًا من الظهر يوم الجمعة. لمعاملات
الحساب المخصصة وتعديل المواقيت، راجع
[صفحة التهيئة في الويكي](https://github.com/0xzer0x/go-pray/wiki/Configuration).

## الاستخدام

عرض الصلاة القادمة:

```sh
go-pray next
```

عرض الموعد القادم لصلاة محددة (`fajr` أو `sunrise` أو `dhuhr` أو `asr` أو `maghrib` أو `isha`):

```sh
go-pray next fajr
```

عرض تقويم الصلاة لليوم، أو لأي تاريخ بصيغة `YYYY-MM-DD` أو `@yesterday` أو `@tomorrow`:

```sh
go-pray calendar
go-pray calendar @tomorrow 2026-12-01
```

استخدم `--format` للاختيار بين المخرجات `short` (الافتراضية) و`table` و`json`.

## الإشعارات

يرسل `go-pray daemon` إشعارًا ويشغّل الأذان عند دخول وقت كل صلاة. شغّله ضمن أوامر
بدء التشغيل في مدير النوافذ. على سبيل المثال، في إعدادات
[Hyprland](https://wiki.hyprland.org/Configuring/):

```ini
exec-once = go-pray daemon
```

## شريط الحالة

### Waybar

المتطلبات:

- `jq`
- [Nerd Font](https://www.nerdfonts.com/)

أضف السكريبت التالي باسم `scripts/go-pray` في
[مجلد إعدادات Waybar](https://github.com/Alexays/Waybar/wiki/Configuration#config-file)،
واجعله قابلًا للتنفيذ:

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

ثم أضف الوحدة إلى إعدادات Waybar:

```json
"custom/go-pray": {
  "interval": 60,
  "return-type": "json",
  "exec": "$HOME/.config/waybar/scripts/go-pray",
  "format": "󱠧  {}",
}
```

تعرض الوحدة الصلاة القادمة، ويعرض التلميح تقويم اليوم. يمكنك تنسيقها في ملف CSS
الخاص بـ Waybar باستخدام اسم الصلاة القادمة كفئة (class)، وهو الاسم بلغة المخرجات
المحددة في `language`.
