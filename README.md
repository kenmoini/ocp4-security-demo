# OpenShift 4 Security Examples

## Bootstrap the Hub Cluster

```bash
# Label Nodes for ODF
oc label --overwrite node/infra-1 cluster.ocs.openshift.io/openshift-storage=""
oc label --overwrite node/infra-2 cluster.ocs.openshift.io/openshift-storage=""
oc label --overwrite node/infra-3 cluster.ocs.openshift.io/openshift-storage=""

# Label Nodes for Egress IPs
oc label nodes app-1 k8s.ovn.org/egress-assignable=""
oc label nodes app-2 k8s.ovn.org/egress-assignable=""
oc label nodes app-3 k8s.ovn.org/egress-assignable=""

# Install the OpenShift GitOps Operator
oc apply -k bootstrap/openshift-gitops/operator/

# Deploy the GitOps Server
oc apply -k bootstrap/openshift-gitops/instance/default/
# or with an Outbound Proxy
oc apply -k bootstrap/openshift-gitops/instance/outbound-proxy/

# Configure the GitOps Server
oc apply -k bootstrap/openshift-gitops/config/

# Set the default storage class
oc annotate --overwrite storageclass/ocs-storagecluster-ceph-rbd storageclass.kubernetes.io/is-default-class="true"
```
