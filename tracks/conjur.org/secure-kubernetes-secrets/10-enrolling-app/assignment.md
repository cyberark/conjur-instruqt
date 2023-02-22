---
slug: enrolling-app
id: zyeexsy2xsc4
type: challenge
title: Enrolling App
teaser: Add the secrets to Conjur
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
In a Secretless Broker deployment, when a client needs access to a Target Service it doesn't try to make a direct connection. Instead, it sends the request through its Secretless Broker.

![secretless broker](https://docs.conjur.org/Latest/en/Content/Resources/Images/secretless_architecture.svg)

The following procedures are covered in this step:

1. Add the secrets to Conjur
2. Add the app to Conjur policy
3. Grant Conjur access to the pods in app namespace
4. Store Conjur SSL cert in a Config Map

## Add the secrets to Conjur

We'll create a layer, create 4 variables as secrets, and grant the layer to access all the variables.

```bash
conjur policy load -b root -f /root/secretless/testapp-policy.yml
```

To review the changes, execute:

```bash
conjur list
```

Now let's save the secrets in Conjur:

```bash
conjur variable set -i app/testapp/secret/password -v "5b3e5f75cb3cdc725fe40318"
```

```bash
conjur variable set -i app/testapp/secret/username -v "test_app"
```

```bash
conjur variable set -i app/testapp/secret/host -v "testapp-db.testapp.svc.cluster.local"
```

```bash
conjur variable set -i app/testapp/secret/port -v "5432"
```
