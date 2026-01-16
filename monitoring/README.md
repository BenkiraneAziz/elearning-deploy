# eLearning & ArgoCD Monitoring Dashboard

This dashboard provides real-time monitoring for your eLearning application and ArgoCD deployment on Scaleway Kubernetes.

## Features

The dashboard includes the following panels:

### eLearning Application
- **App Status**: Shows if your eLearning app pod is running
- **Pod Restarts**: Total number of restarts for the eLearning pods
- **CPU Usage**: Real-time CPU consumption
- **Memory Usage**: Real-time memory consumption
- **Network Traffic**: Incoming (RX) and outgoing (TX) traffic

### ArgoCD
- **ArgoCD Status**: Shows if ArgoCD is healthy and running
- **ArgoCD Pods**: Number of ArgoCD pods running
- **Pods by Phase**: Distribution of ArgoCD pods by their phase (Running, Pending, Failed, etc.)

## How to Import the Dashboard

1. Go to your Scaleway Cockpit dashboard: https://13626354-e9d7-41f8-afcb-e02301521064.dashboard.cockpit.scaleway.com

2. Click on the **"+"** icon in the left sidebar or go to **Dashboards > Import**

3. Click **"Upload JSON file"** or paste the JSON content from `elearning-argocd-dashboard.json`

4. Click **"Load"**

5. Select your Prometheus datasource (should be "Scaleway Metrics - fr-par")

6. Click **"Import"**

## Dashboard Variables

The dashboard uses the following variable:
- **datasource**: Automatically selects your Scaleway Metrics Prometheus datasource

## Refresh Rate

The dashboard is set to auto-refresh every 30 seconds. You can change this in the dashboard settings.

## Metrics Used

The dashboard queries the following Kubernetes metrics:
- `kube_pod_status_phase` - Pod status
- `kube_pod_container_status_restarts_total` - Container restarts
- `container_cpu_usage_seconds_total` - CPU usage
- `container_memory_working_set_bytes` - Memory usage
- `container_network_receive_bytes_total` - Network RX
- `container_network_transmit_bytes_total` - Network TX

## Troubleshooting

If panels show "No data":
1. Ensure your eLearning app pods are running in the `namespace-elearning` namespace
2. Ensure ArgoCD is installed in the `namespace-argocd` namespace
3. Verify that Prometheus is scraping metrics from your cluster
4. Check that the time range is appropriate (default is last 1 hour)

## Customization

You can customize the dashboard by:
- Clicking the panel title and selecting "Edit"
- Modifying the Prometheus queries
- Adjusting thresholds and colors
- Adding new panels with additional metrics
