---
slug: load-policy
id: bhbeqho1xcvo
type: challenge
title: Load Policy
teaser: Load Conjur Policy files into the Conjur service.
notes:
- type: text
  contents: In this challenge, we'll be using the Docker-based Conjur CLI to load
    the policies created in the previous challenge into the Conjur service.
tabs:
- title: Terminal
  type: terminal
  hostname: host01
difficulty: basic
timelimit: 300
---
Now, let's copy the policy files to Docker-based Conjur CLI container and load them.

**Load Root Policy**

```bash
docker cp conjur/conjur.yml root_client_1:/root/
docker-compose exec client conjur policy replace -b root -f /root/conjur.yml
```

**Load Ansible Policy**

```bash
docker cp conjur/ansible.yml root_client_1:/root/
docker-compose exec client conjur policy load -b ansible -f /root/ansible.yml | tee ansible.out
```

**Load Server Policy**

```bash
docker cp conjur/server.yml root_client_1:/root/
docker-compose exec client conjur policy load -b server -f /root/server.yml
```
