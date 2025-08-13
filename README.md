# 🧫 ColabFold Docker Image: CUDA 12.2 + Ubuntu 22.04

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Docker Pulls](https://img.shields.io/docker/pulls/dockerma1993/colabfold)](https://hub.docker.com/r/dockerma1993/colabfold)
[![Architecture](https://img.shields.io/badge/architecture-x86__64-blue)]()

> A ready-to-use Docker image for [**ColabFold**](https://github.com/sokrypton/ColabFold), built on NVIDIA CUDA 12.2 and Ubuntu 22.04, enabling high-performance protein structure prediction with GPU acceleration.

> This image uses the ColabFold MSA server by default for multi-sequence alignment (MSA). If you wish to use a custom MSA server, please refer to the official ColabFold documentation for setup instructions.

> Additionally, if you only need to generate MSAs without running structure prediction, a lightweight CPU-only Docker image is also available for faster and more resource-efficient execution.

## 🚀 Quick Start

### 1. Pull the Docker Image or build yourself

```bash
docker pull dockerma1993/colabfold
or
docker build -t colabfold -f Dockerfile_cuda .
# if you just want to generate msa using colabfold msa api server, you can build whit Dockerfile_msa_only file
docker build -t colabfold -f Dockerfile_msa_only
```

### 2. Run prediction
```bash
# Query the MSA server and predict the structure on local GPU in one go:
colabfold_batch input_sequences.fasta out_dir

# Split querying MSA server and GPU predictions into two steps
colabfold_batch input_sequences.fasta out_dir --msa-only
colabfold_batch input_sequences.fasta out_dir

# generate a json format compatible with AlphaFold3 input using the --af3-json option
colabfold_batch input_sequences.fasta out_dir --msa-only --af3-json
```
