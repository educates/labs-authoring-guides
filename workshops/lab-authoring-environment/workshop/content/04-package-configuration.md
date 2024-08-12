---
title: Package Configuration
---

If you were wishing to install Educates from your own local computer and you did
not already have a Kubernetes cluster available, you could use the `educates
create-cluster` command to create a local Kubernetes cluster using Kind
(Kubernetes in docker). This requires you have the docker runtime installed and
configured appropriately. For this workshop session we will install into the
Kubernetes virtual cluster which as already mentioned has been created for you
for this workshop session.

To install into an existing Kubernetes cluster the CLI command which needs to be
used is `educates admin cluster install`. Before running this command an
appropriate configuration file needs to be created.

For installation of Educates into the virtual cluster created for this workshop
session we will use the following configuration. Clicking on the action block
this time should automatically open the editor and create the file for you.

```editor:append-lines-to-file
file: ~/config.yaml
text: |
    # Specify the infrastructure provider hosting the Kubernetes cluster.

    clusterInfrastructure:
        provider: vcluster

    # Specify the ingress domain to be used to access the workshops hosted by
    # the Educates installation.

    clusterIngress:
        domain: {{< param session_name >}}.{{< param ingress_domain >}}

    # Disable the cluster and security policy engines, and skip installing
    # Kyverno, as policies are enforced by the Educates installation running
    # this workshop session.

    clusterPackages:
        kyverno:
            enabled: false

    clusterSecurity:
        policyEngine: none

    workshopSecurity:
        rulesEngine: none
```

The two key bits of information that we are supplying here are the type of
infrastructure provider and what domain name should be used to access workshops
hosted by the cluster after Educates has been installed.

To make it easier to install Educates into a freshly created Kubernetes cluster
a number of opinionated configurations are provided for different infrastructure
providers, such as EKS (AWS), GKE (GCP) and AKS (Azure). In this case we have
set the provider as `vcluster` corresponding to what would be expected for a
virtual cluster created using the
[vCluster](https://github.com/loft-sh/vcluster) package from [Loft
Labs](https://loft.sh/). 

In the case of the opinionated virtual cluster configuration, it makes for
example the assumption that the virtual cluster was preconfigured to delegate
ingress handling to the underlying Kubernetes cluster, and thus the virtual
cluster doesn't itself require an ingress controller to be installed. In the
case of the opinionated configuration for major IaaS providers, they might
instead automatically install and configure the ingress controller as well, and
if appropriate credentials are provided, the DNS provider for that IaaS could
also be automatically configured to point at the ingress router for the cluster
which is installed.

The aim of the opinionated cluster configurations is thus to take a fresh
Kubernetes cluster and install everything you need to run Educates, as well as
Educates itself.

For this workshop session running in Educates, we set the ingress domain for
our Educates installation to correspond to the ingress domain allocated for
this workshop session.

Other configuration we have included above isn't strictly necessary and
everything will work without supplying it, but since we are using Educates to
demonstrate installation of Educates, we don't need to enable the cluster and
workshop security policy engine, nor install Kyverno which is normally used to
implement such policies, as the underlying Educates installation this workshop
session is running in is already enforcing security policies for everything we
are doing. Disabling this will speed up our installation a bit, but for a real
Educates installation you should keep the security policy engines enabled.
