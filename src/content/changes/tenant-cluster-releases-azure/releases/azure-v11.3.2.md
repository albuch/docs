---
# Generated by scripts/aggregate-changelogs. WARNING: Manual edits to this files will be overwritten.
changes_categories:
- Tenant Cluster Releases for Azure
changes_entry:
  repository: giantswarm/releases
  url: https://github.com/giantswarm/releases/tree/master/azure/archived/v11.3.2
  version: 11.3.2
  version_tag: v11.3.2
date: '2020-06-11T15:00:00+00:00'
description: Release notes for Azure release v11.3.2, published on 11 June 2020, 15:00
title: Tenant Cluster Release v11.3.2 for Azure
---

**If you are upgrading from 11.3.1, upgrading to this release will not roll your nodes. It will only update the apps.**

This release improves the reliability of NGINX Ingress Controller.

Specifically, liveness probe is configured to be more fault tolerant than readiness probe. This helps shed load when it goes beyond replica capacity, speeding up recovery when NGINX gets overloaded.

**Note when upgrading from v11.2.x to v11.3.x:**

This release contains the replacement of CoreOS with Flatcar introduced in v11.3.0. Please carefully read release notes for 11.3.0 including Flatcar OS migration [steps](https://github.com/giantswarm/releases/tree/master/azure/v11.3.0) .

**Note for future v11.3.x releases:**

Please persist this and the above note until all customers are in v11.3.0 and above.

Below, you can find more details on components that were changed with this release.

### nginx-ingress-controller v0.30.0 ([Giant Swarm app v1.6.12](https://github.com/giantswarm/nginx-ingress-controller-app/blob/master/CHANGELOG.md#v1612-2020-06-04))

- Made healthcheck probes configurable.
- Made liveness probe more resilient.

## external-dns v0.5.18 ([Giant Swarm app v1.2.1](https://github.com/giantswarm/external-dns-app/blob/master/CHANGELOG.md#v121-2020-05-29))

- Prefer CNAMEs record sets for AWS SDK configuration with explicit credentials.