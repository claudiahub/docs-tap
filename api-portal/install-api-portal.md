# Install API portal

This document describes how to install API portal
from the Tanzu Application Platform package repository.

>**Note:** Use the instructions on this page if you do not want to use a profile to install packages.
Only the full profile includes API portal.
For more information about profiles, see [Installing the Tanzu Application Platform Package and Profiles](../install.md).

## <a id='prereqs'></a>Prerequisites

Before installing API portal:

- Complete all prerequisites to install Tanzu Application Platform. For more information, see [Installing the Tanzu CLI](../install-general.md).

## <a id='install-api-portal'></a> Install API portal

To install API portal:

1. Check what versions of API portal are available to install by running:

    ```
    tanzu package available list -n tap-install api-portal.tanzu.vmware.com
    ```

    For example:

    ```
    $ tanzu package available list api-portal.tanzu.vmware.com --namespace tap-install
    - Retrieving package versions for api-portal.tanzu.vmware.com...
      NAME                         VERSION  RELEASED-AT
      api-portal.tanzu.vmware.com  1.0.3    2021-10-13T00:00:00Z
    ```

2. (Optional) Make changes to the default installation settings by running:

    ```
    tanzu package available get api-portal.tanzu.vmware.com/VERSION-NUMBER --values-schema --namespace tap-install
    ```

    Where `VERSION-NUMBER` is the version of the package listed in step 1.

    For example:

    ```
    $ tanzu package available get api-portal.tanzu.vmware.com/1.0.3 --values-schema --namespace tap-install
    ```

    For more information about values schema options, see the individual product documentation.

3. Install API portal by running:

    ```
    tanzu package install api-portal -n tap-install -p api-portal.tanzu.vmware.com -v 1.0.3
    ```

    For example:

    ```
    $ tanzu package install api-portal -n tap-install -p api-portal.tanzu.vmware.com -v 1.0.3

    / Installing package 'api-portal.tanzu.vmware.com'
    | Getting namespace 'api-portal'
    | Getting package metadata for 'api-portal.tanzu.vmware.com'
    | Creating service account 'api-portal-api-portal-sa'
    | Creating cluster admin role 'api-portal-api-portal-cluster-role'
    | Creating cluster role binding 'api-portal-api-portal-cluster-rolebinding'
    / Creating package resource
    - Package install status: Reconciling


    Added installed package 'api-portal' in namespace 'tap-install'
    ```

    For more information about API portal, see [API portal for VMware Tanzu](https://docs.pivotal.io/api-portal).