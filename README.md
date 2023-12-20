# OpenShift 4 Security Examples

## Bootstrap the Hub Cluster

```bash
# Install the OpenShift GitOps Operator
oc apply -k bootstrap/openshift-gitops/operator/

# Deploy the GitOps Server
oc apply -k bootstrap/openshift-gitops/instance/default/
# or with an Outbound Proxy
oc apply -k bootstrap/openshift-gitops/instance/outbound-proxy/

# Configure the GitOps Server
oc apply -k bootstrap/openshift-gitops/config/
```

