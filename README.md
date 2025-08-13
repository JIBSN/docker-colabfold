# 🧫 ColabFold Docker Image: CUDA 12.2 + Ubuntu 22.04

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Docker Pulls](https://img.shields.io/docker/pulls/dockerma1993/colabfold)](https://hub.docker.com/r/dockerma1993/colabfold)
[![Architecture](https://img.shields.io/badge/architecture-x86__64-blue)]()

> A ready-to-use **Docker image for ColabFold**, built on **NVIDIA CUDA 12.2** and **Ubuntu 22.04**, enabling high-performance protein structure prediction with GPU acceleration. If you just want to generate MSA using colabfold API, it also has an Docker image without cuda.

This container packages [ColabFold](https://github.com/sokrypton/ColabFold) into a portable Docker environment, allowing you to run fast, accurate protein structure predictions locally — without complex setup.

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
