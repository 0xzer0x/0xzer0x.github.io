---
title: تتبع أوقات الصلاة في مديري النوافذ
summary: تثبيت وتهيئة وحدة مواقيت الصلاة في مدير النوافذ الخاص بك، بما في ذلك شريط الحالة والإشعارات
description: تثبيت وتهيئة وحدة مواقيت الصلاة في مدير النوافذ الخاص بك، بما في ذلك شريط الحالة والإشعارات
date: 2024-09-03
ShowReadingTime: false
hideMeta: true
ShowToc: true
ShowPostNavLinks: false
tags:
  - لينكس
  - مدير النوافذ
  - سكريبتات
  - باش
images: imgs/blogs/statusbar-prayer-times.png
cover:
  image: imgs/blogs/statusbar-prayer-times.png
---

## مقدمة

أحد الفوائد الرئيسية لاستخدام مديري النوافذ هي القدرة على إضافة الوظائف بسهولة
عبر سكريبتات باش. ومن خلال الاستفادة من هذه المرونة، قمت بإنشاء سكريبت باش مصمم
خصيصًا لتتبع أوقات الصلاة. يتكامل هذا السكريبت مع مختلف أشرطة الحالة ووحدات
الإشعارات، مما يوفر طريقة مبسطة للبقاء على علم بأوقات الصلاة مباشرةً من بيئة سطح
المكتب.

## البداية السريعة

لتثبيت سكريبت مواقيت الصلاة بسرعة، اتبع هذه الخطوات:

1. استنساخ المستودع:

```sh
git clone https://github.com/0xzer0x/prayer-times.git
```

2. تشغيل سكريبت التثبيت:

```sh
cd prayer-times
./install.sh
```

## السكريبتات

### المتطلبات الأساسية

قبل استخدام السكريبت، تأكد من تثبيت المتطلبات التالية على نظامك:

- `jq`
- `at`
- `yad`
- `mpv`
- `curl`
- `dunst` (لـ X11)
- `polybar` (لـ X11)
- `mako` (لـ Wayland)
- `waybar` (لـ Wayland)
- [Nerd Font](https://www.nerdfonts.com/) (موصى به)

#### أوبونتو

```bash
sudo apt install jq at yad mpv curl dunst polybar mako waybar
```

#### فيدورا

```bash
sudo dnf install jq at yad mpv curl dunst polybar mako waybar
```

#### آرتش

```bash
sudo pacman -S jq at yad mpv curl dunst polybar mako waybar
```

### التثبيت

يجب عليك نسخ الملفات من [`0xzer0x/prayer-times`](https://github.com/0xzer0x/prayer-times) إلى المسارات التالية:

{{< ltr >}}

- `.local/bin`: `~/.local/bin`
- `.local/share/qatami_takbeer.mp3`: `~/.local/share/qatami_takbeer.mp3`
- `.config/systemd/user`: `~/.config/systemd/user`

{{< /ltr >}}

### التهيئة

لاستخدام سكريبت [`prayer-times`](https://github.com/0xzer0x/prayer-times/blob/main/.local/bin/prayer-times)، يجب عليك تعيين المتغيرات التالية داخل السكريبت:

- `lat`: خط العرض
- `long`: خط الطول
- `method`: طريقة الحساب
- `print_lang`: اللغة لطباعة جدول أوقات الصلاة (`ar`/`en`)
- `notify`: وحدة الإشعارات (`mako`/`dunst`)

### وحدة Systemd

لمزامنة تقويم الصلاة وإنشاء وظائف `at` تلقائيًا، يمكنك تفعيل واحدة من وحدات Systemd التالية بناءً على تفضيلاتك:

- **عند بدء التشغيل:** `systemctl --user enable --now prayer-times.service`
- **عند بدء التشغيل + كل 8 ساعات:** `systemctl --user enable --now prayer-times.timer`

## وحدة شريط الحالة

لإضافة الصلاة التالية إلى شريط الحالة الخاص بك، ستحتاج إلى إضافة وحدة مخصصة إلى تكوين شريط الحالة.

### Polybar

- أضف التالي إلى ملف [إعدادت polybar](https://github.com/polybar/polybar/wiki/Configuration)
- قم بتعديل الألوان حسب تفضيلاتك (استبدل `#83CAFA`)

```ini
[module/prayers]
type = custom/script
exec = $HOME/.local/bin/prayer-times status
interval = 60
label = %{A:$HOME/.local/bin/prayer-times yad:}%{F#83CAFA}󱠧 %{F-} %output%%{A}
```

### Waybar

- أضف الوحدة التالية إلى [إعدادات Waybar](https://github.com/Alexays/Waybar/wiki/Configuration)
- يمكنك تعديل تنسيق الوحدة باستخدام فئة الصلاة التالية (مثل `Asr`)

```json
"custom/prayers": {
"interval": 60,
"return-type": "json",
"exec": "$HOME/.local/bin/prayer-times waybar",
  "on-click": "$HOME/.local/bin/prayer-times yad",
"format": "󱠧 {}",
}
```

## إشعارات الأذان

### Dunst

- أضف القاعدة التالية إلى ملف `dunstrc` الخاص بك

```ini
[play_athan]
summary = "Prayer Times"
script = "$HOME/.local/bin/toggle-athan"
```

### Mako

- أضف القاعدة التالية إلى إعدادات mako

```ini
[summary="Prayer Times"]
on-notify=exec $HOME/.local/bin/toggle-athan
on-button-left=exec $HOME/.local/bin/toggle-athan
```

## نافذة المواقيت

- عنوان النافذة: `Prayers`
- قم بتهيئة مدير النوافذ الخاص بك لعرض نافذة Yad في وضع الطفو وأنت جاهز!
- مثال لقاعدة نافذة لـ [Hyprland](https://hyprland.org/)

```ini
windowrulev2 = float,class:(yad)
windowrulev2 = move cursor -50% 30,title:(Prayers)
```
