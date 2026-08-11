# Navi Cheats for Kubernetes CLI (`kubectl`)

## Features

- Auto-completion for namespaces, pods, deployments, services, secrets, nodes, and more
- Organized into logical sections for daily operations and debugging
- **Safe destructive operations**: Delete commands show a dry-run preview and require confirmation
- Dedicated debugging sections for:
  - Gateway API / Envoy Gateway
  - Cert Manager
  - External Secrets Operator
  - ArgoCD
  - Stakater Reloader
  - Network troubleshooting

## Sections

| Section | Description |
|---------|-------------|
| Cluster Information | Cluster info, nodes, contexts (switch, rename, delete) |
| Node Maintenance | Cordon, uncordon, drain, wait for Ready |
| Namespaces | List, create, delete namespaces |
| Pods | List, describe, logs (container, previous), exec (container, deployment), run interactive pods |
| Deployments | List, describe, rollout restart/status, scale, watch, port-forward |
| Services | List, describe, port-forward (incl. all interfaces) |
| Secrets | List, describe, decode secret values (incl. copy to clipboard) |
| ConfigMaps | List, describe |
| Jobs & CronJobs | List, trigger cronjob manually, job logs, delete |
| Storage (PV & PVC) | List/describe PVCs, PVs, reclaim policies |
| Auth & RBAC | Check permissions with `auth can-i` |
| Kustomize | Apply, delete, preview kustomizations |
| Resource Selection | Query resources by label |
| CRDs & API Resources | List and search CRDs |
| YAML/JSON Output | Get resources as YAML or query with jsonpath |

### Debugging Sections

| Section | Description |
|---------|-------------|
| Gateway API | Gateways, GatewayClasses, HTTPRoutes |
| Envoy Gateway | Proxy pods/logs, SecurityPolicies, ClientTrafficPolicies |
| Cert Manager | Certificates, ClusterIssuers, challenges, orders |
| External Secrets | SecretStores, ExternalSecrets, force-sync, Ready status, operator logs |
| ArgoCD | Port-forward UI, admin password, application sync/health status |
| Reloader | Last-reloaded-from annotation, controller logs |
| Network | Test pods (curl, dns, netshoot), endpoints |
| Node | Describe nodes, resource usage, allocated resources, pods per node |
| Events | Cluster events, warnings |

## Usage

1. Open navi and search for `kubectl`
2. Use arrow keys to navigate commands
3. Most inputs offer interactive selection (namespaces, pods, etc.)
4. Press `Enter` to execute

### Destructive Operations

Delete commands use a safety pattern:
```
namespace "my-app" deleted (dry run)
Execute? [y/N] _
```

You'll see what will be deleted before confirming.

## Examples

```bash
# Port-forward to a service (interactive namespace/service selection)
navi --query "kubectl port-forward"

# View pod logs with label selector
navi --query "kubectl logs label"

# Debug Gateway issues
navi --query "kubectl debug gateway"

# Debug cert-manager
navi --query "kubectl debug certmanager"
```
