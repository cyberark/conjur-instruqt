---
slug: conjur-conn
id: cuhs2gqv4ziw
type: challenge
title: Conjur Connection
teaser: Login to Conjur
notes:
- type: text
  contents: Please wait while we setup the next challenge
tabs:
- title: Jenkins Console
  type: service
  hostname: jenkins-demo
  path: /
  port: 8081
- title: Terminal
  type: terminal
  hostname: jenkins-demo
difficulty: basic
timelimit: 300
---
The following steps define the connection to the Conjur appliance. This is typically a one-time configuration.

You may need to login to Jenkins again after restart.
Jenkins user name is

```text
admin
```

and password is

```text
344827fbdbfb40d5aac067c7a07b9230
```

1. Navigate to `Manage Jenkins > Manage Credentials > (global) > Add Credentials` on the `Jenkins Console` tab, then `Global credentials (unrestricted)` page should be shown

2. On the form that appears, configure the login credentials. These are credentials for the Jenkins host to log into Conjur.

 - Username:

```bash
host/jenkins-frontend/frontend-01
```

 - Password:

  Copy and paste the API key that was returned by Conjur when you loaded the policy declaring this host.
  Forgot it?  No worries, execute the following command to review it:

  ```bash
  cat frontend.out
  ```

3. Click OK.

You can also decide whether to set up global or folder-level access to Conjur, or a combination of both.

To learn more, visit [CyberArk Conjur Doc](https://docs.conjur.org/Latest/en/Content/Integrations/jenkins-configure.htm?tocpath=Integrations%7CJenkins%7C_____2#ConfigureJenkinsConjurconnection)

1. Navigate to either `Jenkins > Manage Jenkins > Configure System` in the `Jenkins Console` tab.

2. Scroll down to `Conjur Appliance`

3. Fill in the form

- Account:

```bash
quick-start
```

- Appliance URL:

```text
http://conjur
```

- Conjur Authn Credential:

```text
host/jenkins-frontend/frontend-01/*****
```

4. Click Save
