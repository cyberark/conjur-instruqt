---
slug: prepare-conjur-client
id: olsnv6liyrfu
type: challenge
title: Prepare Conjur Client
teaser: Setup the Conjur client
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
In this section, we'll configure the following items for setting up the Conjur client:

1. Alias for CLI
2. Reset Admin password
3. Logging in

## Alias for Conjur CLI

Conjur CLI client can be either installed as [binary](https://docs.conjur.org/Latest/en/Content/Tools/CLI_Install_CLI.htm?tocpath=Setup%7C_____2#ruby-gem) or [Docker Container](https://docs.conjur.org/Latest/en/Content/Tools/CLI_Install_CLI.htm?tocpath=Setup%7C_____2#docker-container). In order to have the best of both worlds, we will create an alias to execute the CLI as container.

```bash
export CONJUR_URL=$(kubectl describe svc conjur-cluster-conjur-oss -n conjur-server |grep Endpoints | awk '{print $2}')
export SERVICE_IP=$(echo $CONJUR_URL | awk  -F ':' '{print $1}')

alias conjur='docker run --rm -it --add-host conjur.demo.com:$SERVICE_IP -v $(pwd):/root cyberark/conjur-cli:8 '
```

In your own environment, you may wish to add it in shell script file, e.g. `~/.bashrc` or `~/.zshrc`

## Initalize Conjur CLI

To initialize the client, execute:

```bash
conjur init --url https://conjur.demo.com:9443  --account default --self-signed
```

Trust this certificate:

```text
yes
```

```text
Wrote certificate to /root/conjur-default.pem
Wrote configuration to /root/.conjurrc
```

## Login

Now, we will need to logon to Conjur CLI. Remember the admin API key? Don't worry, we can get it by executing

```bash
grep admin admin.out
```

```bash
conjur login -i admin -p $(grep admin admin.out | cut -c20-)
```

## Reset Admin Password

This step is optional. However, like any other systems, it is highly recommended to change the password regularly. Visit [CyberArk.com](https://cyberark.com/) to learn how CyberArk can help you to develop and deploy effective identity security strategies.

Let's update our admin password to `MySecretP@ss1`

```bash
conjur user change-password -p MySecretP@ss1
```

Next, Log off & on again with the new password `MySecretP@ss1`

```bash
conjur logout && \
conjur login -i admin
```

Please enter admin's password (it will not be echoed):

```text
MySecretP@ss1
```

## Expected output

```text
Logged in
```

Awesome. Now the CLI is setup & admin password has been changed.
