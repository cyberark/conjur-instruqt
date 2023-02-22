---
slug: the-secrets
id: 1e1qaqqxwyzr
type: challenge
title: The Secrets
teaser: Initialize the secret variables previously loaded via Conjur Policy with values.
notes:
- type: text
  contents: In this challenge, we'll be initializing the secret variables creating
    in a previous challenge via Conjur Policy with values using the Docker-based Conjur
    CLI.
tabs:
- title: Terminal
  type: terminal
  hostname: host01
difficulty: basic
timelimit: 300
---

Let's centralize the secrets & server info and add them to Conjur.

**host01**

Host 1 IP:
```
docker-compose exec client conjur variable set -i server/host01/host -v "host01"
```
Host 1 username:

```
docker-compose exec client conjur variable set -i server/host01/user -v "service01"
```
Host 1 password:

```
docker-compose exec client conjur variable set -i server/host01/pass -v "W/4m=cS6QSZSc*nd"
```

**host02**

Host 2 IP:
```
docker-compose exec client conjur variable set -i server/host02/host -v "host02"
```
Host 2 username:
```
docker-compose exec client conjur variable set -i server/host02/user -v "service02"
```
Host 2 password:
```
docker-compose exec client conjur variable set -i server/host02/pass -v "5;LF+J4Rfqds:DZ8"
```