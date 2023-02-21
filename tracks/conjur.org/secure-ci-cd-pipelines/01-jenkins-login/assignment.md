---
slug: jenkins-login
id: 3sqbnsg91o3j
type: challenge
title: Login to Jenkins
teaser: Start by logging in to Jenkins
notes:
- type: text
  contents: Please wait while we setup the next challenge
tabs:
- title: Terminal
  type: terminal
  hostname: jenkins-demo
- title: Conjur UI
  type: service
  hostname: jenkins-demo
  path: /
  port: 8080
- title: Jenkins Console
  type: service
  hostname: jenkins-demo
  path: /
  port: 8081
difficulty: basic
timelimit: 300
---
First, let's make sure that all the containers were started. Run the following command in the `Terminal` and make sure the following containers are returned:

```bash
docker ps
```

* conjur
* conjur-cli
* database
* jenkins
* http-auth-server

If all containers are reported, we're ready to log in to Jenkins.

1. Select the `Jenkins Console` tab.

2. Login as the following username:

```text
admin
```

3. Using the following password:

```text
344827fbdbfb40d5aac067c7a07b9230
```

4. **CHECK THE BOX TO "Keep me signed in"***

5. Click `Sign In`.
