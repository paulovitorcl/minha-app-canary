# Canary Deployment Approaches

This repository contains different approaches for implementing canary deployments with Argo Rollouts.

## Directory Structure

### `ingress-nginx/`
Nginx Ingress Controller approach with header-based routing
- Uses `nginx.ingress.kubernetes.io` annotations
- Supports `X-Canary-Version: canary` header routing
- Requires Nginx Ingress Controller

### `openshift-routes/`
OpenShift Route approaches (no service mesh required)

#### `basic-weighted/`
Basic percentage-based traffic splitting
- Uses OpenShift Route `alternateBackends`
- No header-based routing
- Simple and reliable

#### `header-annotations/`
Attempts header-based routing with HAProxy annotations
- May not work on all clusters (security restrictions)
- Uses custom HAProxy config snippets
- Test before production use

#### `path-based/`
Path-based routing approach
- `/` → stable version
- `/canary` → canary version
- Always works with standard Route features

#### `subdomain-based/`
Subdomain-based routing approach
- `app.domain.com` → stable version
- `canary.app.domain.com` → canary version
- Always works with standard Route features

## Usage

Choose the approach that fits your environment and requirements. All approaches work with Argo Rollouts for managing deployments.