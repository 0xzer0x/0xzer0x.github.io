---
title: سيرة ذاتية
ShowReadingTime: false
hideMeta: true
---

## {{< vcenterico fas user >}} الملف الشخصي

مهندس شغوف بالأتمتة، والبنية التحتية السحابية، والأنظمة القابلة للتوسع. أركّز على تصميم وتشغيل بنية تحتية سحابية (Cloud-Native) على AWS باستخدام Kubernetes وGitOps والبنية التحتية ككود (Infrastructure as Code). تشمل خبرتي تطوير أدوات أتمتة داخلية، وتحسين المعماريات السحابية من حيث التكلفة والكفاءة، وتطوير خطوط CI/CD وسير عمل الحاويات في البيئات الإنتاجية.

## {{< vcenterico fas building >}} الخبرات

{{% job dir="rtl" title="مهندس DevOps" company="ثاندر" from="مايو 2026" to="الآن" location="القاهرة، مصر" %}}

- قدت ترحيل بيئة EGX Staging من البنية التحتية المحلية المعتمدة على K3s وVMs إلى AWS، مع نقل 10 خدمات مصغّرة وأكثر من 7 مكونات تخزينية وخدمية ذات حالة إلى خدمات EKS وEC2 وRDS وElastiCache بنجاح خلال شهر واحد.

{{% /job %}}

{{% job dir="rtl" title="مهندس DevOps" company="سينابس أناليتيكس" from="يوليو 2024" to="مايو 2026" location="هجين / القاهرة، مصر" %}}

- عزّزت أمان 9 خدمات مصغّرة على Kubernetes باستخدام سياسات الشبكة (Network Policies) وسياقات أمان صارمة (Security Contexts)، مما حسّن العزل وقلّل مساحة الهجوم.
- أدرت EKS cluster يستضيف GitLab لأكثر من 30 مهندسًا عبر عدة أقسام، مع ضمان الاستقرار، وتنفيذ التحديثات، ومعالجة المشكلات التشغيلية.
- صمّمت وطوّرت حزمة Python وأداة سطر أوامر (CLI) لتوليد التراخيص والتحقق منها وتوزيعها بشكل آمن، مع تكامل مع AWS KMS وDynamoDB وSSM Parameter Store؛ وتم اعتمادها ضمن 3 منتجات أساسية.
- حسّنت معمارية نشر Azkavision السحابية عبر إزالة التكرار واعتماد خوادم Graviton وحجوزات RDS RI، مما خفّض تكاليف AWS بنسبة 37%.
- طوّرت لوحة Grafana موحّدة لـ 14 خدمة من خدمات Azkavision لمراقبة مؤشرات مستوى الخدمة (SLOs)، بما يشمل أخطاء الواجهة الخلفية، وزمن الاستجابة الأقل من ثانية، ومعدل معالجة خطوط تعلم الآلة، واستهلاك موارد الحاويات.
- أعدت هيكلة أكثر من 20 دورًا في Ansible لتحسين القابلية لإعادة الاستخدام، والمرونة، وسهولة الصيانة طويلة الأمد لأتمتة البنية التحتية.
- خفّضت أحجام صور حاويات تعلم الآلة الخاصة بـ Azkavision بنسبة 28.8% عبر نقل خطوط GitLab CI من Docker-in-Docker إلى Buildah والاستفادة من Dockerfiles متعددة المراحل.

{{% /job %}}

## {{< vcenterico fas graduation-cap  >}} التعليم

{{% job dir="rtl" company="جامعة النيل" title="بكالوريوس علوم الحاسب" from="سبتمبر 2022" to="يونيو 2026" location="الجيزة، مصر" /%}}

## {{< vcenterico fas building >}} الشهادات

- [Kubernetes and Cloud Native Security Associate (KCSA), _The Linux Foundation_](https://www.credly.com/badges/7356a184-2832-4844-a918-cb09078ecae4/public_url)
- [Kubernetes and Cloud Native Associate (KCNA), _The Linux Foundation_](https://www.credly.com/badges/0f2aa22e-73c5-4634-94dd-fa61eb3c86a8/public_url)
- [Certified Kubernetes Security Specialist (CKS), _The Linux Foundation_](https://www.credly.com/badges/28f8fc09-b2d5-4a1d-84b2-440eb2b29d02/public_url)
- [Certified Kubernetes Application Developer (CKAD), _The Linux Foundation_](https://www.credly.com/badges/db19eb80-883a-4f79-a479-22daa438f4ff/public_url)
- [Certified Kubernetes Administrator (CKA), _The Linux Foundation_](https://www.credly.com/badges/579227a3-4587-40ed-b65f-2a44876d0f13/public_url)
- [AWS Certified Solutions Architect - Associate, _Amazon Web Services (AWS)_](https://www.credly.com/badges/140c905e-6216-4f41-9f20-bb38a62979e5/public_url)
- [AWS Certified Developer - Associate, _Amazon Web Services (AWS)_](https://www.credly.com/badges/2f2cff62-d9eb-4c79-ae56-1768be42cbfb/public_url)

## {{< vcenterico fas toolbox >}} الأدوات والتقنيات

{{< rawhtml >}}
{{< ltr >}}

<table class="full-width-table">
  <tr>
    <td>{{< vcenterico simple linux >}}&nbsp;<strong>Linux</strong></td>
    <td>{{< vcenterico simple ansible >}}&nbsp;<strong>Ansible</strong></td>
    <td>{{< vcenterico simple docker >}}&nbsp;<strong>Docker</strong></td>
    <td>{{< vcenterico simple kubernetes >}}&nbsp;<strong>Kubernetes</strong></td>
  </tr>
  <tr>
    <td>{{< vcenterico simple python >}}&nbsp;<strong>Python</strong></td>
    <td>{{< vcenterico simple go >}}&nbsp;<strong>Go</strong></td>
    <td>{{< vcenterico simple yaml >}}&nbsp;<strong>YAML</strong></td>
    <td>{{< vcenterico simple amazonwebservices >}}&nbsp;<strong>AWS</strong></td>
  </tr>
  <tr>
    <td>{{< vcenterico simple git >}}&nbsp;<strong>Git</strong></td>
    <td>{{< vcenterico simple github >}}&nbsp;<strong>GitHub</strong></td>
    <td>{{< vcenterico simple gitlab >}}&nbsp;<strong>GitLab</strong></td>
    <td>{{< vcenterico simple gnubash >}}&nbsp;<strong>Bash</strong></td>
  </tr>
</table>

{{< /ltr >}}
{{< /rawhtml >}}
