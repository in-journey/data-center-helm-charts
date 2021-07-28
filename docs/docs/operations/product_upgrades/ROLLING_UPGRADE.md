# Upgrading application

## Kubernetes update strategies
Kubernetes provides two strategies to update applications managed by `statefulset` controllers:

### Rolling update
The pods will be upgraded one by one until all pods run containers with the updated template. The upgrade is managed by 
Kubernetes and the user has limited control during the upgrade process, after having modified the template. This is the default 
upgrade strategy in Kubernetes. 

To perform a canary or multi-phase upgrade, a partition can be defined on the cluster and Kubernetes will upgrade just 
the nodes in that partition. 

The default implementation is based on *RollingUpdate* strategy with no *partition* defined. 

### Using OnDelete update strategy
In this strategy users select the pod to upgrade by deleting it, and Kubernetes will replace it by creating a new pod
 based on the updated template. To select this strategy the following should be replaced with the current 
 implementation of `updateStrategy` in the `statefulset` spec:

```yaml
  updateStrategy:
    type: OnDelete
```  

## Jira rolling upgrade
To learn about rolling upgrade in Jira see [Jira rolling upgrade](JIRA_UPGRADE.md)

## Confluence rolling upgrade
To learn about rolling upgrade in Confluence see [Confluence rolling upgrade](CONFLUENCE_UPGRADE.md)

## Bitbucket rolling upgrade
To learn about rolling upgrade in Bitbucket see [Bitbucket rolling upgrade](BITBUCKET_UPGRADE.md)

***
* Go back to [README.md](/)
* Go back to the [operation guide](../OPERATION.md)