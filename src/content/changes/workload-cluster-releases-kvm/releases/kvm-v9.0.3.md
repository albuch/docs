---
# Generated by scripts/aggregate-changelogs. WARNING: Manual edits to this files will be overwritten.
aliases:
- /changes/tenant-cluster-releases-kvm/releases/kvm-v9.0.3/
changes_categories:
- Workload Cluster Releases for KVM
changes_entry:
  repository: giantswarm/releases
  url: https://github.com/giantswarm/releases/tree/master/kvm/v9.0.3
  version: 9.0.3
  version_tag: v9.0.3
date: '2020-05-13T19:00:00+00:00'
description: Release notes for KVM release v9.0.3, published on 13 May 2020, 19:00
title: Workload Cluster Release v9.0.3 for KVM
---

This release fixes a rare bug that would prevent the NGINX IC from being installed on a new cluster.

This bug would only occur on cluster creation if you had a nginx-ingress-controller-user-values configmap in the kube-system namespace while the cluster was still initialising.

Solution Engineers have already done the manual fix for affected customers.

## cluster-operator [v0.23.9](https://github.com/giantswarm/cluster-operator/releases/tag/v0.23.9)

- Fix a bug in user values migration logic for apps.