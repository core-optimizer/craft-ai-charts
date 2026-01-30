# Craft AI Charts

[![Helm Release](https://img.shields.io/github/v/release/core-optimizer/craft-ai-charts?label=chart)](https://github.com/core-optimizer/craft-ai-charts/releases)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

Official Helm charts for [Craft AI Platform](https://github.com/core-optimizer/craft-ai-platform) - the Kubernetes-native ML/AI Model Management Platform.

## Usage

### Add the Helm repository

```bash
helm repo add craft-ai https://core-optimizer.github.io/craft-ai-charts
helm repo update
```

### Install the chart

```bash
# Install with default values
helm install craft-ai-platform craft-ai/craft-ai-platform

# Install with custom values
helm install craft-ai-platform craft-ai/craft-ai-platform \
  --namespace craft-ai-system \
  --create-namespace \
  --set dashboard.service.type=NodePort
```

### Verify installation

```bash
kubectl get pods -n craft-ai-system
kubectl get modelspecs
kubectl get modeldeployments -A
```

## Charts

| Chart | Description | Version |
|-------|-------------|---------|
| [craft-ai-platform](./charts/craft-ai-platform) | Craft AI Platform controller and dashboard | 0.1.0 |

## Configuration

See the [values.yaml](./charts/craft-ai-platform/values.yaml) for all available configuration options.

### Common configurations

#### Enable NodePort for dashboard

```yaml
dashboard:
  service:
    type: NodePort
    nodePort: 30080
```

#### Enable Ingress

```yaml
dashboard:
  ingress:
    enabled: true
    className: nginx
    hosts:
      - host: craft-ai.example.com
        paths:
          - path: /
            pathType: Prefix
```

#### Enable Prometheus metrics

```yaml
metrics:
  enabled: true
  serviceMonitor:
    enabled: true
```

## License

Apache 2.0 - See [LICENSE](LICENSE) for details.
