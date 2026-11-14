---
title: Resume
ShowReadingTime: false
hideMeta: true
---

## {{< vcenterico fas user >}} Profile

An engineer at heart with a passion for automation, cloud infrastructure, and scalable systems. I focus on designing and operating cloud-native infrastructure on AWS using Kubernetes, GitOps, and infrastructure as code. My experience includes building internal automation tools, optimizing cloud architectures for cost and efficiency, and improving CI/CD pipelines and container workflows in production environments.

## {{< vcenterico fas building >}} Experiences

{{% job title="DevOps Engineer" company="Thndr" from="May 2026" to="Present" location="Cairo, Egypt" %}}

- Automated TLS certificate issuance and renewal across 6 AWS accounts and the Cloudflare edge, replacing copies in 5+ stores with a GitOps pipeline and expiry monitoring; shipped 2 weeks before a hard expiry, eliminating paid manual renewals.
- Designed and implemented a fine-grained AWS authentication solution for Outpost local clusters combining IAM Roles Anywhere, cert-manager, and SPIFFE, migrating 6 workloads from using node credentials to dedicated, least-privilege permissions.
- Built Thndr Pay’s AWS Outposts EKS platform, integrating 12 infrastructure components via GitOps for PCI readiness.
- Rerouted EGX backoffice traffic via a new ingress path around a faulty component with zero downtime, cutting latency by 66%.
- Led migration of EGX staging environment from on-premise K3s/VMs to AWS, migrating 10 microservices and 7+ stateful components to EKS, EC2, RDS, and ElastiCache within 1 month.

{{% /job %}}

{{% job title="DevOps Engineer" company="Synapse Analytics" from="Jul 2024" to="May 2026" location="Hybrid / Cairo, Egypt" %}}

- Hardened 9 Kubernetes microservices with network policies and strict security contexts, reducing attack surface.
- Operated the EKS-hosted GitLab platform serving 30+ engineers across departments, owning uptime and upgrades.
- Designed and maintained a Python package and CLI for license generation, validation, and secure distribution, integrated with AWS KMS, DynamoDB, and SSM Parameter Store; adopted across 3 core products.
- Cut Azkavision AWS costs by 37% by eliminating architectural redundancy and adopting Graviton instances and RDS RIs.
- Developed a unified Grafana dashboard for 14 Azkavision services, monitoring SLOs for backend errors, sub-second latency, ML pipeline throughput, and container resource utilization.
- Reduced Azkavision ML image sizes by 28.8% by moving GitLab CI from Docker-in-Docker to Buildah with multi-stage builds.

{{% /job %}}

## {{< vcenterico fas diagram-project >}} Projects

{{% job company="Nile Quran Community Platform" title="Quran-centered community platform helping university students" from="Feb 2025" to="Present" %}}

- Engineered the production K3s cluster with Kustomize, ArgoCD, cert-manager, Traefik, Sealed Secrets, and Tailscale.
- Automated the full software delivery lifecycle with 5 GitHub Actions pipelines, taking code from pull request to tested, versioned, and securely deployed production containers.

{{% /job %}}

## {{< vcenterico fas graduation-cap >}} Education

{{% job company="Nile University" title="B.Sc. in Computer Science" from="Sep 2022" to="Jun 2026" location="Giza, Egypt" %}}

- GPA: 3.8/4.0

{{% /job %}}

## {{< vcenterico fas certificate >}} Certificates

- [Kubestronaut (CKA, CKAD, CKS, KCNA, KCSA), _The Linux Foundation_](https://www.credly.com/badges/ab9692b0-04b7-4d33-88c9-6ebb8dc2f26b/public_url)
- [AWS Certified Solutions Architect – Associate, _Amazon Web Services (AWS)_](https://www.credly.com/badges/140c905e-6216-4f41-9f20-bb38a62979e5/public_url)
- [AWS Certified Developer – Associate, _Amazon Web Services (AWS)_](https://www.credly.com/badges/2f2cff62-d9eb-4c79-ae56-1768be42cbfb/public_url)

## {{< vcenterico fas toolbox >}} Skills

- **Containers & Orchestration:** Kubernetes, FluxCD, ArgoCD, Docker, Podman, Buildah, Skopeo
- **Cloud & IaC:** AWS, Huawei Cloud, Terraform, Packer, Terragrunt
- **Systems & Programming:** Linux, Bash, Python, Go, Ansible, Nix
- **Observability:** OpenTelemetry, Prometheus, Thanos, Loki, Grafana, Datadog
- **CI/CD:** GitHub Actions, GitLab CI
