# TODO: Helm-Chart aus Manifesten erstellen

## Vorbereitung
- [x] Helm-Chart-Verzeichnisstruktur anlegen (`nginx-chart/`, `nginx-chart/templates/`)

## Chart-Dateien erstellen
- [x] `Chart.yaml` erstellen (Name, Version, Beschreibung, appVersion)
- [x] `values.yaml` erstellen mit konfigurierbaren Werten:
  - replicaCount
  - image.repository
  - image.tag
  - containerPort

## Templates erstellen
- [x] `templates/_helpers.tpl` erstellen (Hilfsfunktionen für Labels/Namen)
- [x] `templates/deployment.yaml` erstellen (Deployment mit Helm-Variablen)

## Validierung
- [x] `helm lint` ausführen zur Syntax-Prüfung
- [x] `helm template` ausführen zur Überprüfung der generierten Manifeste
