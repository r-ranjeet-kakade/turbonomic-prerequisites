# Turbonomic Prerequisites
Prerequisites to configure your cluster namespace on your RedHat Openshift Console to install the Turbonomic platform Operator from the Operator Hub.
Run the below commands on you Openshift CLI.

## Create a new project namespace _turbonomic_ in Openshift
```console
oc new-project turbonomic
```

## Set the SCC policy to turbonomic service account
```console
oc adm policy add-scc-to-group anyuid system:serviceaccounts:turbonomic
```

## Setup the required roles, role-bindings and service account in _turbonomic_ namespace
```console
oc apply -f https://raw.githubusercontent.com/r-ranjeet-kakade/turbonomic-prerequisites/main/service_account.yaml -n turbonomic
```
```console
oc apply -f https://raw.githubusercontent.com/r-ranjeet-kakade/turbonomic-prerequisites/main/role.yaml -n turbonomic
```
```console
oc apply -f https://raw.githubusercontent.com/r-ranjeet-kakade/turbonomic-prerequisites/main/cluster_role_binding.yaml -n turbonomic
```
```console
oc apply -f https://raw.githubusercontent.com/r-ranjeet-kakade/turbonomic-prerequisites/main/cluster_role.yaml -n turbonomic
```
```console
oc apply -f https://raw.githubusercontent.com/r-ranjeet-kakade/turbonomic-prerequisites/main/role_binding.yaml -n turbonomic
```

## Turbonomic Platform Operator
Install the Turbonomic Platform Operator from the OperatorHub and configure the XL-release by enabling the require targets.
