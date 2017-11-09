- Go to the _IBM Cloud_ main menu and click on **DevOps**, then click on **Toolchains**.

  ![main navigation](main_menu.png?raw=true)
  ![tc](tc.png?raw=true)

- On the next screen, select **Create Toolchain**.

  ![create_tc](create_toolchain.png?raw?true)

- Select the **Simple Cloudfoundry Toolchain** and provide a name in the right (_IBM Cloud_-)organization.

  ![simple_cf](simple_cf_tc.png?raw=true))
  ![tc_name](tc_name.png?raw=true)

- You now need to connect your git repository to that toolchain, so that once you push your code on the command line of your local workstation.

- You may need to authorize _IBM Cloud_ to access your **GitHub** account.

  ![git_auth](git_auth.png)

- The toolchain takes over to process the deployment to _IBM Cloud_.

  ![tc_git](tc_git.png)

- Once you created the toolchain, the individual tools should show **Configured** and the build and deploy steps are triggered automatically.

  ![tc_config](toolchain_config.png)
  ![tc_pipeline](tc_pipeline.png)

- _IBM Cloud_ generates a hostname based on the git repository name, in this case `chat.eu-de.mybluemix.net`. There is a reasonable chance that this name is already taken, so you need to specify our own host name.

  Create a `manifest.yml` with the following content:

  <pre>
  applications:
  - name: <span class="app_name">random-app-name</span>
    memory: 128M
    host: <span class="app_name">random-app-name</span>
  </pre>

  on your local machine. Then manually run `cf push` and verify your app is picking up the right name. _IBM Cloud_ is adding your host to the `eu-de.mybluemix.net` domain  by default so your FQDN is <code><span class="app_name">random-app-name</span>.eu-de.mybluemix.net</code>. Once you can access your hostname, commit and push your changes to git and wait for the pipeline to finish.

{% include random_app_name.html %}
