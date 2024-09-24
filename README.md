# fusion-fleet-upgrade

The current pipeline code can be used to automate Fusion operator upgrade from 2.8.1 to 2.9.

## Pre-requisites
- Install OpenShift Pipeline operator in the cluster where the upgrade is to be run.
- The pipelines will be created under `pipeline-samples` namespace. To use a new namespace, first create/switch to a namespace. Ensure that the `pipeline` service account is present on that namespace. 

To check whether the service account exists, run the following command ensure that the output is non-empty.
```
oc get sa -n <namespace> | grep pipeline
```

After ensuring that the service account exists, go to the `kustomization.yaml` file and change the `namespace` field to the target namespace where the pipeline is to be deployed.


## How to run the script
1. Create a new project or switch to an existing one. Ensure to change the `namespace` field under kustomization.yaml with the same namespace.
```
oc new-project <namespace>
```

2. Run the pipeline
```
oc apply -k .
```

## To delete the pipelines
```
oc delete -k .
```
