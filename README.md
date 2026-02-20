# Kuhl Haus MDP - Market Data Platform

Example code for deploying Kuhl Haus Market Data Platform

## Overview

The Kuhl Haus Market Data Platform (MDP) is a distributed system for collecting, processing, and serving real-time market data. Built on Kubernetes and leveraging microservices architecture, MDP provides scalable infrastructure for financial data analysis and visualization.

### Architecture

The platform consists of four main components:
- **Market data processing library** (`kuhl-haus-mdp`) - Core library with shared data processing logic
- **Backend Services** (`kuhl-haus-mdp-servers`) - Market data listener, processor, and widget service
- **Frontend Application** (`kuhl-haus-mdp-app`) - Web-based user interface and API
- **Deployment Automation** (`kuhl-haus-mdp-deployment`) - Docker Compose, Ansible playbooks and Kubernetes manifests for environment provisioning

### Key Features

- Real-time market data ingestion and processing
- Scalable microservices architecture
- Automated deployment with Ansible and Kubernetes
- Multi-environment support (development, staging, production)
- OAuth integration for secure authentication
- Redis-based caching layer for performance


# Stock Scanner - Docker Configuration

Public Docker Compose and Dockerfile configurations for the stock scanner application detailed in [Part 2 of the blog series](https://the.oldschool.engineer/what-i-built-after-quitting-amazon-spoiler-its-a-stock-scanner-part-2-94e445914951). Pre-built images available for quick deployment with real-time WebSocket market data via Massive.com API.

View [Docker/README.md](./Docker/README.md) to get started.

# Stock Scanner - Ansible/Kubernetes Configuration

The Kuhl Haus Market Data Platform (MDP) is a distributed system for collecting, processing, and serving real-time market data. Built on Kubernetes and leveraging microservices architecture, MDP provides scalable infrastructure for financial data analysis and visualization.


View [ansible/README.md](./ansible/README.md) to get started.

---

# FAQ

**Q: Can I use the free Massive.com tier?**  
A: No. The free Stocks Basic plan lacks WebSocket support required for real-time data. The $29/month Stocks Starter _might_ work but has 15-minute delayed data.

**Q: Do I need to build from source?**  
A: No. The README files references pre-built public images. Only build from source if you're customizing the application.

**Q: Can I customize the scanner logic?**  
A: Yes. Use the `Dockerfile` to build from source with your modifications. See [Part 2 of the blog series](https://the.oldschool.engineer/what-i-built-after-quitting-amazon-spoiler-its-a-stock-scanner-part-2-94e445914951) for building instructions.

---

# Additional Resources

📖 **Blog Series:**
- [Part 1: Why I Built It](https://the.oldschool.engineer/what-i-built-after-quitting-amazon-spoiler-its-a-stock-scanner-28fc3b6d9be0)
- [Part 2: How to Run It](https://the.oldschool.engineer/what-i-built-after-quitting-amazon-spoiler-its-a-stock-scanner-part-2-94e445914951)
- [Part 3: How to Deploy It](https://the.oldschool.engineer/what-i-built-after-quitting-amazon-spoiler-its-a-stock-scanner-part-3-eab7d9bbf5f7)
- [Part 4: Evolution from Prototype to Production](https://the.oldschool.engineer/what-i-built-after-quitting-amazon-spoiler-its-a-stock-scanner-part-4-408779a1f3f2)



# Contributing

Contributions are welcome! Please submit pull requests to the appropriate repository:
- Core library change: [`kuhl-haus-mdp`](https://github.com/kuhl-haus/kuhl-haus-mdp)
- Backend changes: [`kuhl-haus-mdp-servers`](https://github.com/kuhl-haus/kuhl-haus-mdp-servers)
- Frontend changes: [`kuhl-haus-mdp-app`](https://github.com/kuhl-haus/kuhl-haus-mdp-app)
- Deployment improvements: [`kuhl-haus-mdp-deployment`](https://github.com/kuhl-haus/kuhl-haus-mdp-deployment)

---

# License

[MIT License](https://github.com/kuhl-haus/kuhl-haus-mdp-deployment/blob/mainline/LICENSE.txt)

# Support

For questions or issues, please open an issue in the respective repository or contact the maintainers.
