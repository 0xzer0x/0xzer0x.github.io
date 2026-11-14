---
title: Nile Quran Community Platform
summary: Quran-centered community platform helping university students
description: Quran-centered community platform helping university students
date: 2025-02-01
images: imgs/nile-quran-community/social.webp
ShowReadingTime: false
hideMeta: true
ShowToc: false
tags:
  - projects
  - devops
  - kubernetes
cover:
  image: imgs/nile-quran-community/social.webp
---

# {{< vcenterico fas link >}} Links

<div class="grid-container">
<div class="grid-item">

### {{< vcenterico fas server >}} **Infrastructure**

Host provisioning, GitOps setup, and cluster manifests for the platform.

[Infrastructure repository →](https://github.com/nile-quran-community/infra)

</div>
<div class="grid-item">

### {{< vcenterico fas code >}} **Application**

Next.js frontend and Django backend API.

[Frontend →](https://github.com/nile-quran-community/nile-quran-nextjs)<br/>
[Backend →](https://github.com/nile-quran-community/nile-quran-django)

</div>
</div>

# {{< vcenterico fas lightbulb >}} Key Features

{{< rawhtml >}}

<div style="display: flex; gap: 1em;">
    <div>
      <ul>
        <li>Production K3s cluster managed through GitOps with Argo CD</li>
        <li>Host provisioning with Ansible</li>
        <li>TLS certificates from Let's Encrypt with cert-manager</li>
        <li>Public traffic routed through a Traefik Gateway</li>
      </ul>
    </div>
    <div>
      <ul>
        <li>Secrets stored in git as Sealed Secrets</li>
        <li>Argo CD and the backend API reachable only over Tailscale</li>
        <li>5 GitHub Actions pipelines from pull request to tested, versioned, and deployed containers</li>
      </ul>
    </div>
</div>

{{< /rawhtml >}}

# {{< vcenterico fas camera >}} Screenshots

![About page of the Nile Quran Community website](/imgs/nile-quran-community/screenshots/about.webp#center)
![Login page of the Nile Quran Community website](/imgs/nile-quran-community/screenshots/login.webp#center)

# {{< vcenterico fas code >}} Source Code

The platform's source code is available at the [Nile Quran Community GitHub organization](https://github.com/nile-quran-community).
