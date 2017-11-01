---
layout: default
title: Chat App auf Bluemix portieren
---

# {{ page.title }}

## Get the code

Clone your repository to your local disk.

## Create a manifest

Create a new deployment `manifest.yml` file in the cloned directory with the content shown below.
Be sure to provide a name that is unique (globally!!!) and replace the `**********` below:

```
---
applications:
- name: ************
  memory: 512M
  instances: 1
```
This is a fairly simple manifest that should work for you as well. If you need want to check for more options please see https://docs.cloudfoundry.org/devguide/deploy-apps/manifest.html.

## Deploy

Run `bx cf push` to push this to IBM Cloud. 

Once your app is working successfully, proceed to the next step.

## Create a CI/CD pipeline
<tbd>


## Test
