# Github Runners Helm Chart

Este repositorio contiene un Helm Chart que puedes utilizar para desplegar tu aplicación. Sigue los pasos descritos a continuación para desplegar este chart en un registry privado de GitHub.

## Prerrequisitos

Antes de comenzar, asegúrate de cumplir con los siguientes requisitos:

- [Helm](https://helm.sh/docs/intro/install/) instalado (versión 3.0 o superior).
- Tener acceso a un registry de GitHub. Puedes usar el mismo repository de GitHub donde se encuentra este chart o un repository específico para almacenamiento de Helm Charts.

## Pasos para el despliegue

### 1. Autenticarte en el registry de GitHub

Primero, necesitas autenticarte en el registry de GitHub donde se almacenará el chart.

```bash
echo $GITHUB_TOKEN | helm registry login ghcr.io --username <tu-usuario> --password-stdin
```

### 2. Empaquetar el chart

Navega al directorio del chart y empaquétalo utilizando el siguiente comando:

```bash
helm package .
```

### 3. Subir el chart al registry de GitHub

Una vez empaquetado, puedes subir el chart al registry privado de GitHub usando el siguiente comando:

```bash
helm push gha-runner-scale-set-0.9.3.tgz oci://ghcr.io/inchcape-global-devsecops/dso-gh-runners-k8s-helmchart
```