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

Got to the Bluemix main menu ![main navigation](./main_menu.png?raw=true)
and click on `DevOps`.

On the next screen, select `Create Toolchain` ![create_tc](create_toolchain.png?raw?true)

Select the `Simple Cloudfoundry Toolchain` ![simepl_cf](simple_cf_tc.png?raw=true)) and provide a name in the right (Bluemix-)organization ![tc_name](tc_name.png?raw=true).

You now need to connect your git repository to that toolchain, so that once you push your code on the command line of your local workstation, the toolchain takes over to process the deployment to Bluemix ![tc_git](tc_git.png)

Once you created the toolchain, the individual tools should show `Configured` ![tc_config](toolchain_config.png)


## Test
