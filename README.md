# SURF Research Cloud Playbooks

Simple Ansible playbooks for SURF Research Cloud workspaces. Download and run directly on your workspace.

## Structure

```
├── roles/                    # Reusable Ansible roles
│   ├── docker/              # Docker installation
│   ├── nvidia-container-toolkit/  # GPU support
│   ├── ollama/              # Ollama LLM runtime
│   ├── webui/               # Open-WebUI deployment
│   └── n8n/                 # N8N workflow automation
└── playbooks/               # Ready-to-run playbooks
    ├── ollama-webui.yml     # Ollama + Open-WebUI installation
    └── docker-only.yml      # Just Docker installation
```

## Available Playbooks

### Ollama with Open-WebUI (`ollama-webui.yml`)
Complete AI chat setup with Ollama LLM runtime and web interface.

**Quick Start:**
```bash
git clone <this-repo>
cd Research-Cloud-Catalog-Items-DSP
ansible-galaxy collection install -r requirements.yml
ansible-playbook playbooks/ollama-webui.yml
```

**Access:**
- Open-WebUI: http://your-ip:3000
- Ollama API: http://your-ip:11434

### Docker Only (`docker-only.yml`)
Just installs Docker with GPU support.

```bash
ansible-playbook playbooks/docker-only.yml
```

## Customization

Edit variables directly in the playbook files or override with `-e`:

```bash
# Install with N8N workflow automation
ansible-playbook playbooks/ollama-webui.yml -e "install_n8n=true"

# Use different models
ansible-playbook playbooks/ollama-webui.yml -e "ollama_models=['llama3.1:8b','qwen2.5:7b']"
```

## Requirements

- SURF Research Cloud workspace
- Ubuntu 22.04 (standard)
- Ansible installed (`sudo apt install ansible`)
- Sudo privileges
- Internet connection 
