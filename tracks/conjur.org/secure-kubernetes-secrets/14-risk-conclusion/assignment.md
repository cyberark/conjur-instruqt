---
slug: risk-conclusion
id: pxklprpqykda
type: challenge
title: Risk?
teaser: Let's check the risk level now with Secretless Broker implemented
notes:
- type: text
  contents: Please wait while we setup the next challenge
tabs:
- title: Server
  type: terminal
  hostname: server
difficulty: basic
timelimit: 300
---

Let's review the application manifest file:

```bash
cat secretless/testapp-secure.yml
```

And the info for application deployment:

```bash
cat secretless/developer-env.sh
```

Can you find any embedded secret?

No, there is no more embedded secret!
