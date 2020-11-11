# Contoso Cluster Ops

This is an example repository.

- [applications](./apploications): contains an application deployed by an IT operator, e.g. common monitoring or logging agent
- [namespaces](./namespaces): creates three namespaces: `itops`, `team-a`, and `team-b`, these namespaces are managed by the I
- [rbac](./rbac): Kubernetes RBAC configurations
- [team-a](./team-a): contains a ConfigMap produced by IT operator to communicate some configuration to an application team

```console
az k8sconfiguration create \
    --resource-group AzureArc --cluster-name ${CLUSTER_NAME} \
    --name cluster-config --scope cluster \
    --cluster-type connectedClusters \
    --operator-instance-name cluster-config --operator-namespace cluster-config \
    --operator-params "'--git-readonly --registry-disable-scanning --sync-garbage-collection'" \
    --enable-helm-operator false \
    --repository-url https://github.com/slack/cluster-config.git
```
