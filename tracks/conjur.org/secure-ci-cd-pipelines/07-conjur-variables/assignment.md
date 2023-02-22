---
slug: conjur-variables
id: lgsa237f2ajj
type: challenge
title: Conjur Variables
teaser: Declare the variables, privileges, and entitlements
notes:
- type: text
  contents: Please wait while we setup the next challenge
tabs:
- title: Terminal
  type: terminal
  hostname: jenkins-demo
difficulty: basic
timelimit: 300
---

1. Declare the variables, privileges, and entitlements. Copy the following policy as a template:

```bash
docker exec -it conjur-cli sh
cat > jenkins-app.yml << EOF
#Declare the secrets required by the application

- &variables
  - !variable web_password

# Define a group and assign privileges for fetching the secrets

- !group secrets-users

- !permit
  resource: *variables
  privileges: [ read, execute ]
  roles: !group secrets-users

# Entitlements that add the Jenkins layer of hosts to the group

- !grant
  role: !group secrets-users
  member: !layer /jenkins-frontend
EOF
exit
```

This policy does the following:

- Declares the variables to be retrieved by Jenkins.
- Declares the groups that have read & execute privileges on the variables.
- Adds the Jenkins layer to the group. The path name of the layer is relative to root.

Change the variable names, the group name, and the layer name as appropriate.

2. Load the policy into Conjur under the Jenkins policy branch you declared previously:

```bash
docker exec conjur-cli conjur policy load -b jenkins-app -f /jenkins-app.yml
```

### Set variable values in Conjur

Use the Conjur CLI to set variable values.

The CLI command to set a value is:

`conjur variable set -i <policy-path-of-variable-name> -v <secret-value>`

For example:

```bash
docker exec conjur-cli conjur variable set -i jenkins-app/web_password -v NotSoSecureSecret
```
