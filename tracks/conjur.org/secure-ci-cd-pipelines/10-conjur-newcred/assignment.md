---
slug: conjur-newcred
id: sdnkj2rpfepz
type: challenge
title: Conjur New Credential
teaser: Add credentials
notes:
- type: text
  contents: Please wait while we setup the next challenge
tabs:
- title: Jenkins Console
  type: service
  hostname: jenkins-demo
  path: /
  port: 8081
difficulty: basic
timelimit: 300
---
Visit `Jenkins > Demo > Credentials > Folder > Global credentials (unrestricted) > Add Credentials` on the `Jenkins Console` tab to create a new credential

-  Kind: `Conjur Secret Credentials`

-  Variable Path:

  ```text
  jenkins-app/web_password
  ```

- ID:
  ```text
  WEB_PASSWORD
  ```

This is the complete Conjur ID of the variable. This includes the policy path where the variable is defined.

Click "OK" to save it
