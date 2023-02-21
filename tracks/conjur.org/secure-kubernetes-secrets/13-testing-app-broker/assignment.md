---
slug: testing-app-broker
id: 6n3gdvusn8qh
type: challenge
title: Testing the App with Secretless Broker
teaser: Let's make sure the Pets app is up and running
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
Now let's test the app again

## Get the URL

To check whether the app is started & get the endpoint of the service, execute:

```bash
export URL=$(kubectl describe service testapp-secure --namespace=testapp |grep Endpoints | awk '{print $2}' )
```

If a `curl` error is returned, that means the application is still being started.

Please wait for a couple of moments and try again.

## Test the app

To add a new message with a random name, execute:

```bash
curl  -d "{\"name\": \"$(shuf -n 1 /usr/share/dict/american-english)\"}" -H "Content-Type: application/json" $URL/pet
```

Now let's list all the messages by executing:

```bash
curl -s $URL/pets | jq .
```

You can repeat the above actions to create & review multiple messages.
