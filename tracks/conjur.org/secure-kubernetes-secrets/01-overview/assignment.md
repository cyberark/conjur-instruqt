---
slug: overview
id: pfsdjd2tqvrg
type: challenge
title: Overview
teaser: Overview of the tutorial
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
Applications and application developers should be **incapable of leaking secrets**.

To achieve that goal, you’ll play two roles in this tutorial:

1. A **Security Admin** who handles secrets, and has sole access to those secrets
2. An **Application Developer** with no access to secrets.

The situation looks like this:

<a href="#img-1">
  <img alt="Overview" src="../assets/Presentation1.png" />
</a>

<a href="#" class="lightbox" id="img-1">
  <img alt="Overview" src="../assets/Presentation1.png"/>
</a>

Specifically, we will:

**As the security admin:**

1. Setup Conjur in Kubernetes
2. Prepare Conjur Client
3. Enable Authenticator
4. Enrolling App
5. Config Secretless Broker Sidecar

**As the application developer:**

* Deploy the application and the Secretless sidecar

**Prerequisites**

To run through this tutorial, all you need is this course!

Let's get started!

<style>
.lightbox {
  display: none;
  position: fixed;
  justify-content: center;
  align-items: center;
  z-index: 999;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  padding: 1rem;
  background: rgba(0, 0, 0, 0.8);
}

.lightbox:target {
  display: flex;
}

.lightbox img {
  max-height: 100%
}
</style>