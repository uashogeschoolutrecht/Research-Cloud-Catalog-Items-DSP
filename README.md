# SURF Research Cloud Playbooks

Self-contained Ansible playbooks for SURF Research Cloud workspaces. Each playbook includes all necessary tasks and can be run independently.

## Structure

```
├── roles/                          # Reusable Ansible roles (for local development)
└── playbooks/                      # Self-contained playbooks (for SURF RC)
    ├── ollama-webui.yml            # Ollama + Open-WebUI (with collections)
    ├── ollama-webui-simple.yml     # Ollama + Open-WebUI (no collections)
    └── docker-only.yml             # Just Docker installation
```

## Available Playbooks

### Ollama with Open-WebUI
Complete AI chat setup with Ollama LLM runtime and web interface.

**Quick Start (SURF Research Cloud):**
```bash
# This is what SURF Research Cloud will do automatically:
ansible-playbook ollama-webui-simple.yml
```

**For manual installation:**
```bash
git clone <this-repo>
cd Research-Cloud-Catalog-Items-DSP
ansible-playbook playbooks/ollama-webui-simple.yml
```

**Access after installation:**
- Open-WebUI: http://your-ip:3000
- Ollama API: http://your-ip:11434

### Docker Only
Just installs Docker with GPU support.

```bash
ansible-playbook playbooks/docker-only.yml
```

## Playbook Variants

- **`ollama-webui.yml`**: Uses community.docker collection (requires installation)
- **`ollama-webui-simple.yml`**: Uses native docker commands (no extra dependencies)

For SURF Research Cloud, use the `-simple` variant as it has no external dependencies.

## Customization

Edit variables directly in the playbook files or override with `-e`:

```bash
# Install with N8N workflow automation
ansible-playbook playbooks/ollama-webui-simple.yml -e "install_n8n=true"

# Use different models
ansible-playbook playbooks/ollama-webui-simple.yml -e "ollama_models=['llama3.1:8b','qwen2.5:7b']"
```

## Features

- ✅ **Self-contained**: No external roles or collections needed
- ✅ **GPU Support**: Automatic NVIDIA Container Toolkit installation
- ✅ **Docker Compose**: Modern containerized deployment
- ✅ **Multiple Models**: Configurable LLM model installation
- ✅ **Web Interface**: Open-WebUI for easy interaction
- ✅ **Optional N8N**: Workflow automation capabilities

## Requirements

- SURF Research Cloud workspace
- Ubuntu 22.04 (standard)
- Sudo privileges
- Internet connection

## SURF Research Cloud Integration

These playbooks are designed to work with SURF Research Cloud's external plugin system:
1. SURF RC downloads the specific playbook file
2. Runs it with ansible-playbook directly
3. No need for roles, collections, or complex directory structures 
