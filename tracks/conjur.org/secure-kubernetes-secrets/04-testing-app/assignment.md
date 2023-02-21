---
slug: testing-app
id: 16ixbsdgkaov
type: challenge
title: Testing the Application
teaser: Make some calls to test the Pets application
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
## Get the URL

To check whether the app is started & get the endpoint of the service, execute:

```bash
export URL=$(kubectl describe service testapp-insecure --namespace=testapp |grep Endpoints | awk '{print $2}' ) && \
curl $URL/pets && echo
```

If a `curl` error is returned, that means the application is still being started. Please wait for a couple of moments and try again. It should return [] if the application is up.

## Test the app

To add a new message with a random name, execute:

```bash
curl -d "{\"name\": \"$(shuf -n 1 /usr/share/dict/american-english)\"}" -H "Content-Type: application/json" $URL/pet && echo
```

Now let's list all the messages by executing:

```bash
curl -s $URL/pets | jq . && echo
```

You can repeat the above actions to create & review multiple messages.
