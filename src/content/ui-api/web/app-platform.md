---
linkTitle: App platform
title: The Giant Swarm App Platform in the web interface
description: What the Giant Swarm App Platform looks like on our web interface and how to use it.
last_review_date: 2020-04-22
weight: 30
menu:
  main:
    parent: uiapi-web
aliases:
  - /reference/web-interface/app-catalog/
  - /reference/web-interface/app-platform/
owner:
  - https://github.com/orgs/giantswarm/teams/team-batman
---

# The Giant Swarm App Platform in the web interface

This page will give you an overview of what parts of the Giant Swarm App Platform
are managable using our web interface.

If you'd like to know more about the App Platform in general, go here for an
[overview of the Giant Swarm App Platform]({{< relref "/app-platform" >}}) instead.

## Viewing all App Catalogs

Our web interface lets you browse the App Catalogs installed on your Control Plane.
Click on "App Catalogs" in the navigation menu. The "App Catalogs" link will only
be visible if your Control Plane has at least one App Catalog installed on it.

The screenshot below shows what the "App Catalogs" page looks like with two app catalogs
installed:

![A screenshot of our web interface, showing a list of available app catalogs](/img/app-catalogs.png)

## Installing an App

Click on the catalog you'd like to install from. Only apps in the Managed catalog
will be monitored and managed by us.

![A screenshot of our web interface, showing a list of apps in an app catalog](/img/apps.png)

Once you know what app you'd like to install, click on that app, and then on
"Configure & Install"

![A screenshot of our web interface, showing the detail page for a specific app, in this case grafana](/img/app-detail-page.png)

That'll bring up a modal where you can choose what cluster you want to install
the app on, the version you want install, as well as some further steps allowing you to configure the app.

This is also where you can provide your [values.yaml](https://helm.sh/docs/chart_template_guide/values_files/) with custom configuration for the app.

![A screenshot of the configuration screen when install an app using our web interface](/img/app-configuration-modal.png#width-60)

Apps can be configured by uploading optional YAML files, one intended for general configuration values and the other
for secret values.

Configuration is split into values and secrets so that you are able to manage values that are shareable from values
that requires more care in handling.

Configuration values exist at three levels: `catalog`, `cluster`, and `user`, but the
web interface only allows you to upload files for the final (`user`) level.

The values are merged with values from previous configuration levels and override them
when they contain the same key.

Communication between the web interface and the api that processes these files is protected by SSL/TLS.
Data stored in etcd is encrypted at rest.

When you upload a file the API creates a ConfigMap or a secret respectively
and sets the `userConfig` values in the App CR to reference the ConfigMap or secret
that was just created.

See our [app configuration reference page]({{< relref "/app-platform/app-configuration" >}}) for more details and examples.

## Editing the version of an App

Once an app is installed, it is also possible to change the version.

Go to cluster that the app is on, click on the "Apps" tab, and then click on the
app you would like to edit.

Once there you should see a dropdown that you can use to pick a different version.

![A screenshot showing where you can edit the app's version](/img/app-version-picker.png#width-60)
