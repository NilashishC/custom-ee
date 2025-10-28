# Ansible Execution Environment Definition

This directory contains the definition files for an Ansible Execution Environment Definition.

## Files Generated

- `execution-environment.yml` - Main EE definition file


## Configuration

### Base Image
- **Base Image**: `registry.access.redhat.com/ubi9/python-311:latest`

## Building the Execution Environment

To build this Execution Environment Definition, run:

```bash
ansible-builder build -t custom-ee-2:latest -f execution-environment.yml --container-runtime podman
```

## Prerequisites

- [ansible-builder](https://ansible-builder.readthedocs.io/) installed
- Container runtime (Podman or Docker)

## Usage

Once built, you can use this Execution Environment with:

```bash
# Run with ansible-navigator
ansible-navigator run playbook.yml --execution-environment-image custom-ee-2:latest

# Or with ansible-runner
ansible-runner run . -p playbook.yml --container-imagecustom-ee-2:latest
```

## Customization

You can modify the `custom-ee-2.yaml` file to add additional dependencies or build steps as needed.
