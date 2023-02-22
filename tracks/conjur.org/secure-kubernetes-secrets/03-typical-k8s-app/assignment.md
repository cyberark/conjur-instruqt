---
slug: typical-k8s-app
id: ackxras16yky
type: challenge
title: Typical Kubernetes Application
teaser: Deploy the application
notes:
- type: text
  contents: Please wait while we setup the next challenge
tabs:
- title: Server
  type: terminal
  hostname: server
difficulty: basic
timelimit: 300
---
## Typical Kubernetes Application

  Let's deploy an app.

## Database

  Let's setup a database for the application

  ```bash
  kubectl apply -f db/db.yml
  ```

## App

  We will make use of the pet store demo app from CyberArk [Pet Store Demo](https://github.com/conjurdemos/pet-store-demo) as an example.

  To deploy, execute:

```bash
kubectl apply -f insecure/app.yml
```

  Now the application has been installed.

  Let's wait for it to be started, run the command:

```bash
kubectl get pods -n testapp -w
```

Expected output
===============

```text
  master $ kubectl get pods -n testapp -w
  NAME                                READY   STATUS    RESTARTS   AGE
  testapp-db-6b6958ccf6-tmzlq         0/1     Pending   0          10s
  testapp-insecure-846bdf65db-dbwsj   0/1     Pending   0          10s
  testapp-insecure-846bdf65db-dbwsj   0/1     Pending   0          17s
  testapp-db-6b6958ccf6-tmzlq         0/1     Pending   0          17s
  testapp-insecure-846bdf65db-dbwsj   0/1     Pending   0          28s
  testapp-db-6b6958ccf6-tmzlq         0/1     Pending   0          28s
  testapp-insecure-846bdf65db-dbwsj   0/1     ContainerCreating   0          28s
  testapp-db-6b6958ccf6-tmzlq         0/1     ContainerCreating   0          28s
  testapp-db-6b6958ccf6-tmzlq         1/1     Running             0          62s
  testapp-insecure-846bdf65db-dbwsj   1/1     Running             0          71s
```

Wait for both `testapp-db` & `testapp-app` to have `Running` status. Press `Ctrl-C` to stop.
