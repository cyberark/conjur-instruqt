---
slug: risk
id: x0dm8l2zhb2u
type: challenge
title: The Risk
teaser: See the danger of embedded credentials in configuration
notes:
- type: text
  contents: Please wait while we setup the next challenge
tabs:
- title: Server
  type: terminal
  hostname: server
difficulty: basic
timelimit: 600
---
When we deploy the application, the database secret is embedded in the configuration.

```bash
cat insecure/app.yml && echo
```

Can you find it? It's at the end of the configuration.

```text
  - name: DB_USERNAME
    value: test_app
  - name: DB_PASSWORD
    value: 5b3e5f75cb3cdc725fe40318
```

Who has reviewed it? When did it happen? Can you track it?

Yup, that's the risk we're talking about.

Let's fix it!
