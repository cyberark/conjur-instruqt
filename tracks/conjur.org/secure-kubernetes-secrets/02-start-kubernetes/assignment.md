---
slug: start-kubernetes
id: tqave01oen1s
type: challenge
title: Start Kubernetes
teaser: Let's prepare the environment and start Kubernetes running
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
The kubernetes environment has been prepared for you. Let's start by creating a script file to start Kubernetes, if its not running:

```bash
cat > launch.sh <<EOF
#!/bin/bash

echo Waiting for Kubernetes to start...
  while [ ! -f /root/.kube/config ]
  do
    sleep 1
  done
echo Kubernetes started
if [ -f /root/.kube/start ]; then
  /root/.kube/start
fi

EOF

chmod +x launch.sh
```

Let's run the script:

```bash
./launch.sh && echo
```

If you get the following message on the Server tab that means kubernetes is starting. It will take a minute or two.

> root@server:/# launch.sh
>
> Waiting for Kubernetes to start...

When it shows ```Kubernetes started```, we're ready to proceed! 😁
