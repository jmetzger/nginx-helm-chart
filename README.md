# Nginx Helm Chart

Ein einfaches Helm Chart für Nginx Deployments in Kubernetes.

## Projektstruktur

```
.
├── manifests/
│   └── deploy.yaml          # Original Kubernetes Manifest
└── nginx-chart/
    ├── Chart.yaml           # Chart Metadaten
    ├── values.yaml          # Konfigurierbare Werte
    └── templates/
        ├── _helpers.tpl     # Helper-Funktionen
        ├── deployment.yaml  # Deployment Template
        └── service.yaml     # Service Template
```

## Konfigurierbare Werte

| Parameter | Beschreibung | Default |
|-----------|--------------|---------|
| `replicaCount` | Anzahl der Pods | `8` |
| `image.repository` | Container Image | `nginxinc/nginx-unprivileged` |
| `image.tag` | Image Tag | `1.27` |
| `image.pullPolicy` | Image Pull Policy | `IfNotPresent` |
| `containerPort` | Container Port | `8080` |
| `service.type` | Service Typ | `ClusterIP` |
| `service.port` | Service Port | `80` |
| `resources` | Resource Limits/Requests | `{}` |

## Installation

```bash
# Standard-Installation
helm install my-nginx ./nginx-chart

# Mit eigenem Namespace
helm install my-nginx ./nginx-chart -n nginx --create-namespace

# Mit angepassten Werten
helm install my-nginx ./nginx-chart \
  --set replicaCount=3 \
  --set image.tag="1.28"

# Mit NodePort Service
helm install my-nginx ./nginx-chart --set service.type=NodePort
```

## Upgrade

```bash
helm upgrade my-nginx ./nginx-chart --set replicaCount=5
```

## Deinstallation

```bash
helm uninstall my-nginx
```

## Validierung

```bash
# Syntax prüfen
helm lint ./nginx-chart

# Template rendern (ohne Installation)
helm template my-nginx ./nginx-chart
```

## Entwicklung

Das Chart wurde aus dem Original-Manifest `manifests/deploy.yaml` erstellt und um folgende Features erweitert:

- Konfigurierbare Replicas, Image und Ports über `values.yaml`
- Standard Kubernetes Labels (app.kubernetes.io/*)
- Service für Pod-Zugriff
- Helper-Funktionen für konsistente Naming-Konventionen
