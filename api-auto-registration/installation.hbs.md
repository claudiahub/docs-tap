# Install API Auto Registration

This document describes how to install API Auto Registration from the Tanzu Application Platform package repository.

>**Note:** Use the instructions on this page if you do not want to use the full or run profile to install packages.
The "full" and "run" profiles includes API Auto Registsration by default.
For more information about profiles, see [About Tanzu Application Platform components and profiles](../about-package-profiles.md).

## <a id='prereqs'></a>Prerequisites

Before installing API Auto Registration:

- Complete all prerequisites to install Tanzu Application Platform. For more information, see [Prerequisites](../prerequisites.md).

## <a id='parameters'></a>Parameters
API Auto Registration uses the following parameters in `tap-values.yaml`

```yaml
api_auto_registration:
  tap_gui_url: <URL TO TAP GUI>
  cluster_name: <CLUSTER NAME AS SHOWN IN LIFECYCLE>
```

>**Note:** The value of `cluster_name` is what you will see in the `lifecycle` property of your API Entities within TAP GUI. The value should be unique for each cluster. 

If you are installing TAP with run or full profile you will get the following default values, but keep in mind you can override them if need be.

```yaml
api_auto_registration:
  tap_gui_url: http://server.tap-gui.svc.cluster.local:7000 
  cluster_name: <Value from shared.ingressDomain or 'dev' if not found>
```

When using a mutli-cluster installation using the run cluster profile or without a profile you will need to set the `api_auto_registration.tap_gui_url` parameters correctly for successful entity registration with TAP GUI, and you are strongly recommended to set `cluster_name` to a unique value for each run cluster.

You can locate the `tap_gui_url` by going to the view cluster with the TAP GUI you want to register the entity with and executing the following commands

```console
kubectl get secret tap-values -n tap-install -o jsonpath="{.data['tap-values\.yaml']}" | base64 -d | yq '.tap_gui.app_config.backend.baseUrl'  
``` 

## <a id='prereqs'></a>Prerequisites

Before installing API Auto Registration:

- Complete all prerequisites to install Tanzu Application Platform. For more information, see [Prerequisites](../prerequisites.md).

- Located the TAP GUI url using the instructions mentioned above  

## <a id='install'></a>Install

To install API Auto Registration:

1. List version information for the package by running:

    ```console
    tanzu package available list apis.apps.tanzu.vmware.com --namespace tap-install
    ```

    Example output:

    ```console
     NAME                             VERSION        RELEASED-AT
     apis.apps.tanzu.vmware.com       0.1.0          2022-08-09 16:27:06 -0400 EDT
    ```  

2. Create a config file named `api-auto-registration-config.yaml`.

    Add the following entry into your `api-auto-registration-config.yaml` file.
    ```yaml
    tap_gui_url: YOUR-TAP-GUI-URL
    cluster_name: YOUR-CLUSTER-NAME
    ```

>**Note:** The value of `cluster_name` is what you will see in the `lifecycle` property of your API Entities within TAP GUI 

3. Install the package using the Tanzu CLI
   
   ```console
   tanzu package install api-auto-registration 
   --package-name apis.apps.tanzu.vmware.com
   --namespace $(TAP_NAMESPACE)
   --version $(VERSION)
   --values-file api-auto-registration-config.yaml
   --wait=true
   ``` 