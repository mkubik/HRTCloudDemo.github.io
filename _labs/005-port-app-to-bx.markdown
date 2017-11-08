---
layout: default
title: Port the Chat App to IBM Cloud
---

# {{ page.title }}

## Get the code

Clone your repository to your local disk.

## Create a manifest

Create a new deployment `manifest.yml` file in the cloned directory with the content shown below. Be sure to provide a name that is unique within the domain ''.

<pre>
---
applications:
- name: <span class="app_name">random-app-name</span>
  memory: 512M
  instances: 1
</pre>


This is a fairly simple manifest that should work for you as well. If you need want to check for more options please see the [documentation] (https://docs.cloudfoundry.org/devguide/deploy-apps/manifest.html).

## Deploy

Run `bx cf push` to push this to IBM Cloud. Only proceed to the next step if your app is working correctly.

## Create a CI/CD pipeline

{% include pipeline.markdown %}

## Test

Try to access the url you provided by the `manifest.yml`
