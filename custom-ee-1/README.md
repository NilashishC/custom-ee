# Ansible Execution Environment Definition

This directory contains the definition files for an Ansible Execution Environment Definition.

## Files Generated

- `execution-environment.yml` - Main EE definition file
- `requirements.txt` - Python package requirements
- `bindep.txt` - System package requirements
- `requirements.yml` - Ansible Galaxy collection requirements


## Configuration

### Base Image
- **Base Image**: `registry.access.redhat.com/ubi9/python-311:latest`

### Ansible Collections (9)
- `cisco.asa` (v2.0.0)
- `ansible.posix`
- `community.general`
- `community.crypto`
- `cisco.nxos` (v1.2.4)
- `cisco.ios` (v2.0.0)
- `amazon.aws`
- `ansible.mcp_builder`
- `ansible.mcp`

### Python Requirements (3)
- `paramiko`
- `requests>2.1.0`
- `pydantic>=2.0.0`

### System Packages (1)
- `libssh-devel`

## Building the Execution Environment

To build this Execution Environment Definition, run:

```bash
ansible-builder build -t custom-ee-1:latest -f execution-environment.yml --container-runtime podman
```

## Prerequisites

- [ansible-builder](https://ansible-builder.readthedocs.io/) installed
- Container runtime (Podman or Docker)

## Usage

Once built, you can use this Execution Environment with:

```bash
# Run with ansible-navigator
ansible-navigator run playbook.yml --execution-environment-image custom-ee-1:latest

# Or with ansible-runner
ansible-runner run . -p playbook.yml --container-imagecustom-ee-1:latest
```

## Customization

You can modify the `custom-ee-1.yaml` file to add additional dependencies or build steps as needed.
