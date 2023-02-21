---
slug: enable-authenticator
id: ankjmgl3etzj
type: challenge
title: Enable Authenticator
teaser: Configure the Authenticator
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
Let's enable the kubenetes authenicator for application deployment.

The following procedures are covered in this step.

1. Policy
2. Initalize CA
3. Configure Authenticator

We will use the following configuration in this tutorial:

| Configuration    | Value   |
|------------------|---------|
| AUTHENTICATOR_ID | dev     |
| CONJUR_ACCOUNT   | default |
| TEST_APP_NAMESPACE_NAME | testapp
| APPLICATION_SERVICE_ACCOUNT | testapp-secure-sa |
| AUTHENTICATOR_CLIENT_CONTAINER_NAME | secretless |

For details, please refer to the [Conjur official doc](https://docs.conjur.org/Latest/en/Content/Integrations/Kubernetes_deployApplicationCluster.htm?tocpath=Integrations%7COpenShift%252C%20Kubernetes%7C_____4)

## Policy

### Policy for human users

At least one user needs write permission to load policy and variables into Conjur. This is standard Conjur policy that creates an administrative group of users for Conjur.
A sample policy is prepared.
To review it, execute:

```bash
cat conjur/policy_for_human_users.yml
```

### Policy for authentication identities

The identities that will be used to authenticate and retrieve secrets from Conjur will also need to be defined in policy and added to the layer that was granted access to the Kubernetes authenticator webservice in the previous policy.

For details about the different identities that can be used in this policy, see [Application Identity in OpenShift/Kubernetes](https://docs.conjur.org/Latest/en/Content/Integrations/Kubernetes_AppIdentity.htm)

A sample policy is prepared.

To review it, execute:

```bash
cat conjur/policy_for_authenticator_identities.yml
```

### Policy for the Kubernetes authenticator service

Conjur uses policy to allowlist the applications that have access to the Kubernetes authenticator and store the values necessary to create client certificates for mutual TLS
A sample policy is prepared.

To review it, execute:

```bash
cat conjur/policy_for_k8s_authenticator_service.yml
```

### Load Policies into Conjur

To load all 3 policies into Conjur, execute:

```bash
conjur policy load root /root/conjur/policy_for_human_users.yml && \
conjur policy load root /root/conjur/policy_for_authenticator_identities.yml && \
conjur policy load root /root/conjur/policy_for_k8s_authenticator_service.yml
```

## Initalize CA

The [Policy for the Kubernetes authenticator service](https://docs.conjur.org/Latest/en/Content/Integrations/Kubernetes_deployApplicationCluster.htm?tocpath=Integrations%7COpenShift%252C%20Kubernetes%7C_____4#Define2) declares variables to hold a CA certificate and key.

To review the script, execute:

```bash
cat conjur/initialize_ca.sh
```

To initialize the CA, execute:

```bash
source conjur/initialize_ca.sh
```

## Configure Conjur authenticators

We have setup the conjur authenicators during Conjur setup!

To verify, execute:

```bash
export POD_NAME=$(kubectl get pods --namespace conjur-server \
   -l "app=conjur-oss,release=conjur-cluster" \
   -o jsonpath="{.items[0].metadata.name}")
kubectl exec --namespace conjur-server  $POD_NAME  --container=conjur-oss -- env | grep CONJUR_AUTHENTICATORS
```
