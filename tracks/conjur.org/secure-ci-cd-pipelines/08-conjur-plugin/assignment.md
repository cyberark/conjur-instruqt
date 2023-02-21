---
slug: conjur-plugin
id: kdpkuyirkahw
type: challenge
title: Conjur Plugin
teaser: Add the Conjur Plugin for Jenkins
notes:
- type: text
  contents: Declare the variables, privileges, and entitlements
tabs:
- title: Terminal
  type: terminal
  hostname: jenkins-demo
- title: Jenkins Console
  type: service
  hostname: jenkins-demo
  path: /
  port: 8081
difficulty: basic
timelimit: 300
---
1. Download the `Conjur.hpi` file from <https://github.com/cyberark/conjur-credentials-plugin/releases>

2. Navigate to `Jenkins -> Manage Jenkins -> Manage Plugins -> Advanced` in the `Jenkins Console` tab.
3. In the Deploy Plugin section, browse for the downloaded copy of `Conjur.hpi`.

4. Click `Deploy`

5. After the upload is complete, give the following command in the `Terminal` tab:

```bash
docker restart jenkins
```
