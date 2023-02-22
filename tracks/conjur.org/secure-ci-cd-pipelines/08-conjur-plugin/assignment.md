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

1. Navigate to `Jenkins -> Manage Jenkins -> Manage Plugins -> Available plugins` in the `Jenkins Console` tab.

2. Search for the `Conjur Secrets` plugin and click `Install without restart`.

3. After the install is complete, run the following command in the `Terminal` tab:

```bash
docker restart jenkins
```
