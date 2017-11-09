---
layout: lab
title: Port the Chat App to IBM Cloud
---

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
<br/><br/>
This is a fairly simple manifest that should work for you as well. If you need want to check for more options please see https://docs.cloudfoundry.org/devguide/deploy-apps/manifest.html.


This is a fairly simple manifest that should work for you as well. If you need want to check for more options please see the [documentation] (https://docs.cloudfoundry.org/devguide/deploy-apps/manifest.html).

## Deploy

Run `bx cf push` to push this to IBM Cloud. Only proceed to the next step if your app is working correctly.

## Create a CI/CD pipeline

- Go to the _IBM Cloud_ main menu
and click on **DevOps**, then click on **Toolchains** <br/><br/>![main navigation](main_menu.png?raw=true)![tc](tc.png?raw=true)<br/><br/>
- On the next screen, select **Create Toolchain** <br/> <br/>![create_tc](create_toolchain.png?raw?true)<br/><br/>
- Select the **Simple Cloudfoundry Toolchain**
and provide a name in the right (_IBM Cloud_-)organization<br/> <br/>![simepl_cf](simple_cf_tc.png?raw=true))<br/>![tc_name](tc_name.png?raw=true).<br/><br/>
- You now need to connect your git repository to that toolchain, so that once you push your code on the command line of your local workstation.<br/><br/>
- You may need to authorize _IBM Cloud_ to access your **GitHub** account.<br/><br/>![git_auth](git_auth.png)<br/><br/>
- The toolchain takes over to process the deployment to _IBM Cloud_.<br/><br/>![tc_git](tc_git.png)<br/><br/>
- Once you created the toolchain, the individual tools should show **Configured** and the build and deploy steps are triggered automatically.<br/><br/>![tc_config](toolchain_config.png)<br/>![tc_pipeline](tc_pipeline.png)<br/><br/>
- _IBM Cloud_ generates a hostname based on the git repository name, in this case `chat.mybluemix.net`. There is a reasonable chance that this name is already taken, so we need to work around this.<br/>Create a `manifest.yml` with the following content:
  <pre>
      ---
      applications:
      - name: WhoChats
        memory: 128M
        host: <span class="app_name">whochats</span>
  </pre>

    on your local machine. Then manually run <code>cf push</code> and verify your app is picking up the right name. _IBM Cloud_ is adding your host to the <code>mybluemix.net</code> domain  by default so your FQDN is <code>[host].mybluemix.net</code>. Once you can access your hostname, commit and push your changes to git and wait for the pipeline to finish.<br/><br/>

## Test
- Try to access [<code>https://<span class="app_name">xxx</span>.mybluemix.net</code>](https://<span class="app_name">xxx</span>.mybluemix.net)

## References
 * [Create a Toolchain](https://console.bluemix.net/docs/toolchains/toolchains_overview.html)

{% include pipeline.markdown %}

<script type="text/javascript" src="{{ site.baseurl }}/js/random-app-name.js"></script>
<script type="text/javascript">
  var app_name = random_app_name();
  var spans = document.getElementsByClassName("app_name");
  for (i = 0; i < spans.length; i++) {
      var span = spans[i];
      span.parentNode.replaceChild(document.createTextNode(app_name), span);
  }
</script>
