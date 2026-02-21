[![License](https://img.shields.io/github/license/kuhl-haus/kuhl-haus-mdp-deployment)](https://github.com/kuhl-haus/kuhl-haus-mdp-deployment/blob/mainline/LICENSE.txt)
[![GitHub issues](https://img.shields.io/github/issues/kuhl-haus/kuhl-haus-mdp-deployment)](https://github.com/kuhl-haus/kuhl-haus-mdp-deployment/issues)
[![GitHub pull requests](https://img.shields.io/github/issues-pr/kuhl-haus/kuhl-haus-mdp-deployment)](https://github.com/kuhl-haus/kuhl-haus-mdp-deployment/pulls)

# kuhl-haus-mdp-deployment

Deployment automation for the Kuhl Haus Market Data Platform.

## Overview

Infrastructure-as-code for deploying the Market Data Platform across development, staging, and production environments. Includes Docker Compose configurations for local development, Ansible playbooks for provisioning, and Kubernetes manifests for production deployment.

## Getting Started

### Docker Compose (Local Development)

Pre-built images are available for quick deployment with real-time WebSocket market data via the Massive.com API.

See [Docker/README.md](./Docker/README.md) to get started.

### Ansible / Kubernetes (Production)

Ansible playbooks and Kubernetes manifests for multi-environment provisioning and deployment.

See [ansible/README.md](./ansible/README.md) to get started.

## Deployment Components

| Component | Description |
|---|---|
| **Docker/** | Docker Compose configurations and Dockerfiles for local development |
| **ansible/** | Ansible playbooks for Kubernetes cluster provisioning and application deployment |
| **monitoring/** | Observability stack configuration (OpenObserve, OpenTelemetry) |
| **scripts/** | Utility scripts for deployment automation |

## FAQ

**Q: Can I use the free Massive.com tier?**
A: No. The free Stocks Basic plan lacks WebSocket support required for real-time data. The $29/month Stocks Starter _might_ work but has 15-minute delayed data.

**Q: Do I need to build from source?**
A: No. The Docker README references pre-built public images. Only build from source if you're customizing the application.

**Q: Can I customize the scanner logic?**
A: Yes. Use the Dockerfile to build from source with your modifications. See [Part 2 of the blog series](https://the.oldschool.engineer/what-i-built-after-quitting-amazon-spoiler-its-a-stock-scanner-part-2-94e445914951) for building instructions.

## Code Organization

The platform consists of four main packages:

- **Market data processing library** ([kuhl-haus-mdp](https://github.com/kuhl-haus/kuhl-haus-mdp)) — Core library with shared data processing logic
- **Backend Services** ([kuhl-haus-mdp-servers](https://github.com/kuhl-haus/kuhl-haus-mdp-servers)) — Market data listener, processor, and widget service
- **Frontend Application** ([kuhl-haus-mdp-app](https://github.com/kuhl-haus/kuhl-haus-mdp-app)) — Web-based user interface and API
- **Deployment Automation** ([kuhl-haus-mdp-deployment](https://github.com/kuhl-haus/kuhl-haus-mdp-deployment)) — Docker Compose, Ansible playbooks and Kubernetes manifests for environment provisioning *(this repo)*

## Documentation

For architecture details, component descriptions, and API reference, see the
[full documentation on Read the Docs](https://kuhl-haus-mdp.readthedocs.io/en/latest/).

## Additional Resources

📖 **Blog Series:**

- [Part 1: Why I Built It](https://the.oldschool.engineer/what-i-built-after-quitting-amazon-spoiler-its-a-stock-scanner-28fc3b6d9be0)
- [Part 2: How to Run It](https://the.oldschool.engineer/what-i-built-after-quitting-amazon-spoiler-its-a-stock-scanner-part-2-94e445914951)
- [Part 3: How to Deploy It](https://the.oldschool.engineer/what-i-built-after-quitting-amazon-spoiler-its-a-stock-scanner-part-3-eab7d9bbf5f7)
- [Part 4: Evolution from Prototype to Production](https://the.oldschool.engineer/what-i-built-after-quitting-amazon-spoiler-its-a-stock-scanner-part-4-408779a1f3f2)

## Contributing

Contributions are welcome! Please submit pull requests to the appropriate repository:

- Core library changes → [kuhl-haus-mdp](https://github.com/kuhl-haus/kuhl-haus-mdp)
- Backend changes → [kuhl-haus-mdp-servers](https://github.com/kuhl-haus/kuhl-haus-mdp-servers)
- Frontend changes → [kuhl-haus-mdp-app](https://github.com/kuhl-haus/kuhl-haus-mdp-app)
- Deployment improvements → [kuhl-haus-mdp-deployment](https://github.com/kuhl-haus/kuhl-haus-mdp-deployment)
