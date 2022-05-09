# turbonomic-prerequisites
Prerequisites to configure your cluster namespace on your RedHat Openshift Console to install the Turbonomic platform Operator from the Operator Hub.

# Create a new project namespace
oc new-project turbonomic

# Set the SCC policy to turbonomic service account
oc adm policy add-scc-to-group anyuid system:serviceaccounts:turbonomic

# Setup the required roles, role-bindings and service account
oc apply -f service_account.yaml -n turbonomic
oc apply -f role.yaml -n turbonomic
oc apply -f role_binding.yaml -n turbonomic
oc apply -f cluster_role.yaml -n turbonomic
oc apply -f cluster_role_binding.yaml -n turbonomic

# Turbonomic Platform Operator
Install the Turbonomic Platform Operator from the OperatorHub and configure the XL-release by enabling the require targets.
