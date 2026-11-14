---
title: منصة مقرأة النيل
summary: منصة مجتمع قرآني تعين طلاب الجامعة
description: منصة مجتمع قرآني تعين طلاب الجامعة
date: 2025-02-01
images: imgs/nile-quran-community/social.webp
ShowReadingTime: false
hideMeta: true
ShowToc: false
tags:
  - مشاريع
  - ديف أوبس
  - كوبرنيتيس
cover:
  image: imgs/nile-quran-community/social.webp
---

# {{< vcenterico fas link >}} الروابط

<div class="grid-container">
<div class="grid-item">

### {{< vcenterico fas server >}} **البنية التحتية**

تجهيز الخادم، وإعداد GitOps، وملفات تعريف العنقود الخاصة بالمنصة.

[مستودع البنية التحتية ←](https://github.com/nile-quran-community/infra)

</div>
<div class="grid-item">

### {{< vcenterico fas code >}} **التطبيق**

واجهة أمامية باستخدام Next.js وواجهة برمجية خلفية باستخدام Django.

[الواجهة الأمامية ←](https://github.com/nile-quran-community/nile-quran-nextjs)<br/>
[الواجهة الخلفية ←](https://github.com/nile-quran-community/nile-quran-django)

</div>
</div>

# {{< vcenterico fas lightbulb >}} الميزات الرئيسية

{{< rawhtml >}}

<div style="display: flex; gap: 1em;">
    <div>
      <ul>
        <li>عنقود K3s للإنتاج يُدار عبر GitOps باستخدام Argo CD</li>
        <li>تجهيز الخادم باستخدام Ansible</li>
        <li>شهادات TLS من Let's Encrypt باستخدام cert-manager</li>
        <li>توجيه الزيارات العامة عبر بوابة Traefik</li>
      </ul>
    </div>
    <div>
      <ul>
        <li>حفظ الأسرار في git على هيئة Sealed Secrets</li>
        <li>لا يمكن الوصول إلى Argo CD والواجهة الخلفية إلا عبر Tailscale</li>
        <li>5 خطوط GitHub Actions من طلب الدمج حتى حاويات مختبرة ومُرقّمة الإصدار ومنشورة</li>
      </ul>
    </div>
</div>

{{< /rawhtml >}}

# {{< vcenterico fas camera >}} لقطات شاشة

![صفحة التعريف بموقع مقرأة النيل](/imgs/nile-quran-community/screenshots/about.webp#center)
![صفحة تسجيل الدخول في موقع مقرأة النيل](/imgs/nile-quran-community/screenshots/login.webp#center)

# {{< vcenterico fas code >}} الشيفرة المصدرية

الشيفرة المصدرية للمنصة متاحة في [منظمة مقرأة النيل على GitHub](https://github.com/nile-quran-community).
