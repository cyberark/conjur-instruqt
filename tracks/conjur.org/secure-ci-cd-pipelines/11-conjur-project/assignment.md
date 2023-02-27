---
slug: conjur-project
id: syf0ycnltjft
type: challenge
title: Conjur Project
teaser: Create a new project
notes:
- type: text
  contents: Please wait while we setup the next challenge
tabs:
- title: Jenkins Console
  type: service
  hostname: jenkins-demo
  path: /
  port: 8081
- title: Terminal
  type: terminal
  hostname: jenkins-demo
difficulty: basic
timelimit: 300
---
Let's test the setup by copying & updating the project

1. To create a new project, go back to `Demo` & click `New Item`

 - Enter an item name:

   ```text
   Secure Freestyle Project
   ```
 - Type:

   ```text
   Freestyle Project
   ```

2. Click OK

3. Next, we need to add a new binding.
   Check `Use secret text(s) or files(s)` under `Build Environment`

4. Under `Binding`, click `Add > Conjur Secret Credentials`

- Variable:

  ```text
  WEB_PASSWORD
  ```

- Credentials > Specific credentials: `ConjurSecret:jenkins-app/web_password/*Conjur*()`

1. Click the `Build Steps` tab in the sidebar

2. Click `Add build step > Execute shell`

   Command to add:

   ```bash
   curl -Is -u theServerAccount:$WEB_PASSWORD http://http-auth-server
   ```

3. Click Save

4. Let's verify the setup by clicking "Build Now".
