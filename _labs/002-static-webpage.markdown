---
layout: default
title: Run a static webpage on _IBM Cloud_
---

# {{ page.title }}

## Create a simple HTML file

1.  Create a new directory that will hold the files for the new web site
1.  In that directory, create a new file `index.html` with the following content:
    ```html
    <!DOCTYPE html>
    <html>
    <head>
      <title>HRT Static Webpage Example</title>
    </head>
    <body>
    The content of the document...
    </body>
    </html>
    ```
1.  Preview the file in a web browser and edit until you are happy with it.

## Deploy

1.  Logon to the IBM Cloud using `cf`:

    ```bash
    cf login -a https://api.eu-gb.bluemix.net
    ```

    Provide your username and password and select the organization and space.
    If no space exists yet, create one using `cf create-space dev -o $ORG_NAME`, where `$ORG_NAME` is the name of the org you choose on first login. This is typically your email address.

1.  Push the app:

    <pre>
    cf push <span id="app_name">random-app-name</span> -b staticfile_buildpack
    </pre>

1.  Observe the output and look for the line starting with `urls:`. This line tells you the fully-qualified domain name of the started application. Open it in a browser and verify that the page looks just like when you opened it locally.

## References

* Cloud Foundry Documentation: [Staticfile Buildpack](https://docs.cloudfoundry.org/buildpacks/staticfile/index.html)

<script type="text/javascript" src="{{ site.baseurl }}/js/random-app-name.js"></script>
<script type="text/javascript">
  var span = document.getElementById("app_name");
  span.parentNode.replaceChild(document.createTextNode(random_app_name()), span);
</script>
