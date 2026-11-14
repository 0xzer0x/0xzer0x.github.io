---
title: Kubernetes The Ansible Way
summary: Bootstrap a Kubernetes cluster from scratch, the Ansible way
description: Bootstrap a Kubernetes cluster from scratch, the Ansible way
date: 2024-07-13
images: imgs/kubernetes-the-ansible-way/banner.webp
ShowReadingTime: false
hideMeta: true
ShowToc: false
tags:
  - projects
  - devops
  - kubernetes
  - ansible
cover:
  image: imgs/kubernetes-the-ansible-way/banner.webp
---

# {{< vcenterico fas download >}} Get Started

<div class="grid-container">
<div class="grid-item">

### {{< vcenterico fas terminal >}} **Vagrant & Ansible**

Clone the repository and run `vagrant up` to create the virtual machines and deploy the whole cluster.

[Instructions →](https://github.com/0xzer0x/kubernetes-the-ansible-way?tab=readme-ov-file#get-started)

</div>
<div class="grid-item">

### {{< vcenterico fab youtube >}} **Demo**

Watch the cluster being deployed from start to finish.

[Demo video →](https://youtu.be/nikDHKM5pcA)

</div>
</div>

# {{< vcenterico fas lightbulb >}} Key Features

{{< rawhtml >}}

<div style="display: flex; gap: 1em;">
    <div>
      <ul>
        <li>Automates every step of Kubernetes the Hard Way</li>
        <li>Two control plane nodes behind an HAProxy load balancer</li>
        <li>Creates and signs certificates for every component</li>
        <li>Generates kubeconfigs for the cluster</li>
      </ul>
    </div>
    <div>
      <ul>
        <li>Prepares nodes with the required kernel modules</li>
        <li>Installs the containerd container runtime</li>
        <li>Cluster networking with Flannel</li>
        <li>Internal DNS with CoreDNS</li>
      </ul>
    </div>
</div>

{{< /rawhtml >}}

# {{< vcenterico fas code >}} Source Code

Kubernetes The Ansible Way source code is available at the project's [GitHub repository](https://github.com/0xzer0x/kubernetes-the-ansible-way).
