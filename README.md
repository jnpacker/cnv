# CONTAINER NATIVE VIRTUALIZATION

This repository has different artifacts for enabling CNV (Container Native Virtualization) in the OpenShift cluster fleet.

## CONTENTS
### [... What to know before you begin](#before-you-begin)
### [... OperatorPolicy kind for deploying CNV](#installing-with-operatorpolicy)
### ... DEMO'ng with KVM_EMULATION
### ... Importing a CNV hosting cluster
### ... Viewing the fleet

## Before you begin
1. `ACM Hub` refers to an OpenShift cluster with Red Hat Advanced Cluster Management for Kubernetes installed
2. `CNV` refers to Container Native Virtualization from Red Hat
3. `RHOV` refers to Red Hat OpenShift Virtualization
4. `Operator` Red Hat packaging of sofware for OpenShift
5. `ManagedCluster` is an OpenShift or STaR-K8s cluster that has the ACM agent and agent addons running on it (the cluster is managed by ACM).
6. `Virtual Machine` software based container with an OS running in it that mimics and HW computer(server).

## INSTALLING WITH OPERATORPOLICY
The OperatorPolicy allows you to install/activate CNV on any ACM ManagedCluster by just adding an label: `acm_cnv: "true"`.  This installs and sets up the CNV operator and the hyperconverged custom resource on a ManagedCluster.  After this OperatorPolicy applies, the target cluster can manage virtual machines and ACM will discover and allow the user to interact with these virtual machines. 

1. Apply the following YAML to install the CNV OperatorPolicy
   ```
   kubectl apply -f https://github.com/stolostron/cnv/sample/cnv-op-kind.yaml
   ```
2. To use the newly installed CNV OperatorPolicy, add the label `acm-cnv: "true"` to any ManagedCluster (Note... This only works for OpenShift ManagedClusters)

