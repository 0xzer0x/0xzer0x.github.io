---
title: سيرة ذاتية
ShowReadingTime: false
hideMeta: true
---

## {{< vcenterico fas user >}} الملف الشخصي

مهندس شغوف بالأتمتة، والبنية التحتية السحابية، والأنظمة القابلة للتوسع. أركّز على تصميم وتشغيل بنية تحتية سحابية (Cloud-Native) على AWS باستخدام Kubernetes وGitOps والبنية التحتية ككود (Infrastructure as Code). تشمل خبرتي تطوير أدوات أتمتة داخلية، وتحسين المعماريات السحابية من حيث التكلفة والكفاءة، وتطوير خطوط CI/CD وسير عمل الحاويات في البيئات الإنتاجية.

## {{< vcenterico fas building >}} الخبرات

{{% job title="مهندس DevOps" company="ثاندر" from="مايو 2026" to="الآن" location="القاهرة، مصر" %}}

- أتمتّ إصدار وتجديد شهادات TLS عبر 6 حسابات AWS وشبكة Cloudflare، واستبدلت نُسخها المحفوظة في أكثر من 5 مواضع بخط GitOps مع مراقبة لمواعيد انتهائها؛ وسلّمت الحل قبل أسبوعين من موعد انتهاء حتمي، مما ألغى التجديدات اليدوية المدفوعة.
- صمّمت ونفّذت حلًا للمصادقة مع AWS بصلاحيات دقيقة لعناقيد Outposts المحلية، يجمع بين IAM Roles Anywhere وcert-manager وSPIFFE، ونقلت 6 أحمال عمل من استخدام بيانات اعتماد العُقد إلى صلاحيات مخصّصة وفق مبدأ الحد الأدنى من الامتيازات.
- أنشأت منصة EKS على AWS Outposts لخدمة Thndr Pay، ودمجت 12 مكوّنًا للبنية التحتية عبر GitOps للجاهزية للامتثال لمعيار PCI.
- أعدت توجيه حركة مرور نظام EGX الإداري عبر مسار دخول جديد يتجاوز مكوّنًا معطوبًا دون أي توقف للخدمة، مما خفّض زمن الاستجابة بنسبة 66%.
- قدت ترحيل بيئة EGX Staging من البنية التحتية المحلية المعتمدة على K3s وVMs إلى AWS، مع نقل 10 خدمات مصغّرة وأكثر من 7 مكونات ذات حالة إلى EKS وEC2 وRDS وElastiCache خلال شهر واحد.

{{% /job %}}

{{% job title="مهندس DevOps" company="سينابس أناليتيكس" from="يوليو 2024" to="مايو 2026" location="هجين / القاهرة، مصر" %}}

- عزّزت أمان 9 خدمات مصغّرة على Kubernetes باستخدام سياسات الشبكة (Network Policies) وسياقات أمان صارمة (Security Contexts)، مما قلّل مساحة الهجوم.
- أدرت منصة GitLab المستضافة على EKS والتي يستخدمها أكثر من 30 مهندسًا عبر عدة أقسام، وتوليت مسؤولية استقرارها وتحديثاتها.
- صمّمت وطوّرت حزمة Python وأداة سطر أوامر (CLI) لتوليد التراخيص والتحقق منها وتوزيعها بشكل آمن، مع تكامل مع AWS KMS وDynamoDB وSSM Parameter Store؛ وتم اعتمادها ضمن 3 منتجات أساسية.
- خفّضت تكاليف AWS الخاصة بـ Azkavision بنسبة 37% عبر إزالة التكرار في المعمارية واعتماد خوادم Graviton وحجوزات RDS RI.
- طوّرت لوحة Grafana موحّدة لـ 14 خدمة من خدمات Azkavision لمراقبة مؤشرات مستوى الخدمة (SLOs)، بما يشمل أخطاء الواجهة الخلفية، وزمن الاستجابة الأقل من ثانية، ومعدل معالجة خطوط تعلم الآلة، واستهلاك موارد الحاويات.
- خفّضت أحجام صور حاويات تعلم الآلة الخاصة بـ Azkavision بنسبة 28.8% عبر نقل GitLab CI من Docker-in-Docker إلى Buildah مع البناء متعدد المراحل.

{{% /job %}}

## {{< vcenterico fas diagram-project >}} المشاريع

{{% job company="منصة مقرأة النيل" title="منصة مجتمع قرآني تعين طلاب الجامعة" from="فبراير 2025" to="الآن" %}}

- هندست عنقود K3s للإنتاج باستخدام Kustomize وArgoCD وcert-manager وTraefik وSealed Secrets وTailscale.
- أتمتّ دورة تسليم البرمجيات بالكامل عبر 5 خطوط GitHub Actions، تنقل الشيفرة من طلب الدمج إلى حاويات إنتاجية مختبرة ومُرقّمة الإصدار ومنشورة بشكل آمن.

{{% /job %}}

## {{< vcenterico fas graduation-cap >}} التعليم

{{% job company="جامعة النيل" title="بكالوريوس علوم الحاسب" from="سبتمبر 2022" to="يونيو 2026" location="الجيزة، مصر" %}}

- المعدل التراكمي: 3.8/4.0

{{% /job %}}

## {{< vcenterico fas certificate >}} الشهادات

- [Kubestronaut (CKA, CKAD, CKS, KCNA, KCSA), _The Linux Foundation_](https://www.credly.com/badges/ab9692b0-04b7-4d33-88c9-6ebb8dc2f26b/public_url)
- [AWS Certified Solutions Architect – Associate, _Amazon Web Services (AWS)_](https://www.credly.com/badges/140c905e-6216-4f41-9f20-bb38a62979e5/public_url)
- [AWS Certified Developer – Associate, _Amazon Web Services (AWS)_](https://www.credly.com/badges/2f2cff62-d9eb-4c79-ae56-1768be42cbfb/public_url)

## {{< vcenterico fas toolbox >}} المهارات

- **الحاويات وتنسيقها:** Kubernetes، FluxCD، ArgoCD، Docker، Podman، Buildah، Skopeo
- **السحابة والبنية التحتية ككود:** AWS، Huawei Cloud، Terraform، Packer، Terragrunt
- **الأنظمة والبرمجة:** Linux، Bash، Python، Go، Ansible، Nix
- **المراقبة والرصد:** OpenTelemetry، Prometheus، Thanos، Loki، Grafana، Datadog
- **CI/CD:** GitHub Actions، GitLab CI
