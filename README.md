# Dgraph Thoth Config

This is the Configuration of Dgraph deployment on OpenShift for project Thoth.

## How To Use it

Deploying Dgraph on OpenShift depends upon requirements.Based on Non-High Availability or High Availability Dgraph is needed:

Start with dgraph image, import the dgraph image to the openshift namespace.(use the [imagestream openshift template](./openshift/dgraph-imagestream))

- High Availability:

  - Deploy Zero : Use the [Zero OpenShift Template](./openshift/dgraph-zero.yaml)
  - Deploy Alpha: Use the [Alpha OpenShift Template](./openshift/dgraph-alpha.yaml)

- Non High Availability:

  - Deploy Non HA: Use the [Dgraph Non-HA OpenShift Template](./openshift/dgraph-non-ha.yaml)

PVC are created with creation of zero's and alpha's.

Prometheus Metrics: Deploy prometheus exporter to gather dgraph metrics.(Use the [prom exporter template](./openshift/dgraph-prometheus-exporter.yaml)). Dgraph Metrics documentation: [Docs](https://docs.dgraph.io/deploy/#metrics)

**Note**:

- To re-setup the dgraph deployment. Delete the following resources:<br>
  pods, statefulsets, services, persistentvolumeclaims, persistentvolumes.<br>
  Then use the deployment steps to setup.
- For scale down instructions use the following [operations docs](https://github.com/thoth-station/thoth-ops/blob/master/docs/dgraph_operations.md).

## References

- [Dgraph documentation](https://docs.dgraph.io/deploy/)
- [Dgraph deployment on kubernetes](https://docs.dgraph.io/deploy/#using-kubernetes-v1-8-4)
- [Deployment templates for Dgraph on kubernetes](https://github.com/dgraph-io/dgraph/tree/master/contrib/config/kubernetes)
