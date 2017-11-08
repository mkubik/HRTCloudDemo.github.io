---
layout: lab
title: Consuming Cloud Services
---

## Introduction

In this exercise you will instantiate an instance of the Watson Tone Analyzer Service and connect it to a simple app that is provided to you.
The Watson Tone Analyzer Service is able to detect moods and tones in a text submitted to it.

The purpose of this exercise is to enable you to configure and use existing cloud services to add value to your application without much work.

The IBM Cloud provides multiple services for areas like artificial intelligence (aka Watson), Internet of things and many areas more.

## Subscribe to the IBM Tone Analyzer Service

- Go to the _IBM Cloud_ main menu
and click on **Catalog**, then select **Watson** in the menu on the left side and click on **Tone Analyzer**
<br><br>![catalog](lab4_catalog.png?raw=true)![watson](lab4_watson.png?raw=true)![tone](lab4_tone_tile.png?raw=true)<br><br>

- On the next page leave all default values as they are and click **Create**

- After beeing redirected the Tone Anayzer page the service is now ready to use

- Retrieve the credentials for your service instance

    1. Click Service credentials.
    2. Click View credentials under Actions.
    3. Copy the username, password and values.

- Note the values to be used in the next section

## Get the code of the sample app

The provides sample app uses the Watson Tone Analyzer service to provide an simple API and user interface to score lines of text as happy or unhappy.  

- Fork the git repository https://github.com/HRTCloudDemo/HRTToneDemo into your own Github account by pressing the **Fork** button in that Github Repository

  ![fork](lab4_fork.png?raw=true)

- Copy the URL of your repository from the GitHub UI
![clone](lab4_clone.png?raw=true)


- Clone your fork of the repository to your local disk
git clone <url from the last step> and change into the created folder

- copy the file **.env.sample** and save it under the new name **.env**

- edit the new file **.env** and fill in username, password and url of your instance of the Tone Analyzer service

- test the app locally
  - Install dependent packages via ```npm -i```
  - Start the app via ```node app.js```
  - You can open the app by visiting http://localhost:3000 in your browser
  - Submitting with all defaults should return "happy" in the mood field

![toneapp](lab4_toneapp.png?raw=true)

- push the working app to IBM Cloud
  - set the API endpoint to your region

    ```bx api api.eu-de.bluemix.net```
  - login into the IBM Cloud

    ```bx login```

  - target your organisation and space

    ```bx target -o <YOUR ORG> -s <YOUR SPACE>```

  - deploy your app to the cloud

    <code>
    cf push <span class="app_name">random-app-name</span>
    </code>

  - access the app in your Browser via

    ``` https://<appname from the cd push command>.eu-de.bluemix.net```

  - Submitting with all defaults should return "happy" in the mood field


<script type="text/javascript" src="{{ site.baseurl }}/js/random-app-name.js"></script>
<script type="text/javascript">
  var app_name = random_app_name();
  var spans = document.getElementsByClassName("app_name");
  for (i = 0; i < spans.length; i++) {
      var span = spans[i];
      span.parentNode.replaceChild(document.createTextNode(app_name), span);
  }
</script>
