# Install Out of the Box Templates

This document describes how to install Out of the Box Templates
from the Tanzu Application Platform package repository.

>**Note:** Use the instructions on this page if you do not want to use a profile to install packages.
Both the full and light profiles include Out of the Box Templates.
For more information about profiles, see [Installing the Tanzu Application Platform Package and Profiles](../install.md).

The Out of the Box Templates package is used by all the Out of the Box Supply
Chains to provide the templates that are used by the Supply Chains to create
the objects that drive source code all the way to a deployed application in a
cluster.

## <a id='ootb-templ-prereqs'></a>Prerequisites

Before installing Out of the Box Templates:

- Complete all prerequisites to install Tanzu Application Platform. For more information, see [Installing the Tanzu CLI](../install-general.md).
- Install cartographer. For more information, see [Install Supply Chain Choreographer](install-scc.md).
- Install [Tekton Pipelines](../tekton/install-tekton.md).

## <a id='inst-ootb-templ-proc'></a> Install

As this package has no extra configurations to be provided, all it takes to
install it is the following command:

```
tanzu package install ootb-templates \
  --package-name ootb-templates.tanzu.vmware.com \
  --version 0.5.1 \
  --namespace tap-install
```

This results in:

```
\ Installing package 'ootb-templates.tanzu.vmware.com'
| Getting package metadata for 'ootb-templates.tanzu.vmware.com'
| Creating service account 'ootb-templates-tap-install-sa'
| Creating cluster admin role 'ootb-templates-tap-install-cluster-role'
| Creating cluster role binding 'ootb-templates-tap-install-cluster-rolebinding'
| Creating package resource
/ Waiting for 'PackageInstall' reconciliation for 'ootb-templates'
/ 'PackageInstall' resource install status: Reconciling


 Added installed package 'ootb-templates' in namespace 'tap-install'
```