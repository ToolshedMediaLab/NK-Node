# NK Node

<img width="1024" height="576" alt="NK_Node_Showcase_BlackBars" src="https://github.com/user-attachments/assets/061364ff-9bee-4ffa-a272-27a3627fda04" />

---

**Remote local-AI inference for NeuraKiln.**

NK Node turns another NVIDIA-equipped Windows PC into a dedicated inference provider for **NeuraKiln**, without requiring you to manually manage server commands, endpoint addresses, model switching infrastructure, or runtime configuration after every reboot.

It is designed for one job:

> **Make another PC's GPUs available to NeuraKiln with as little friction as possible.**

NK Node is not a separate chat application and is not intended to duplicate NeuraKiln's model-management or conversation interface.

---

## What NK Node Does

NK Node provides a lightweight management layer around the local inference stack used by NeuraKiln.

It handles tasks such as:

- Hosting LLM inference on another PC
- Automatically discovering and pairing with NeuraKiln
- Restoring saved server configuration after restart
- Managing supported inference backends
- Managing `llama-swap`
- Managing model locations and runtime configuration
- Updating supported runtime components
- Starting and restarting the inference stack without rebuilding your setup manually
- Allowing NeuraKiln to use GPUs installed in another machine on your network

Once paired, NeuraKiln can treat the NK Node machine as an available inference provider.

---

## Why NK Node Exists

A dedicated inference PC is useful.

Repeatedly administering one is not.

Without NK Node, a multi-PC local AI setup can involve repeatedly managing:

- Runtime builds
- Launch commands
- Server configuration
- Ports and endpoints
- Model paths
- `llama-swap`
- Runtime updates
- Reboots
- Connection information

NK Node packages that repetitive administration into a dedicated application.

The goal is not to create another layer of complexity.

The goal is to remove one.

---

# NeuraKiln Integration

NK Node is designed to integrate directly with **NeuraKiln**.

Instead of manually copying server URLs or entering connection information, NeuraKiln and NK Node can discover and pair with one another.

### Typical setup

```text
┌──────────────────────────────┐
│          Main PC             │
│                              │
│         NeuraKiln            │
│             │                │
└─────────────┼────────────────┘
              │
              │ Local Network
              │
┌─────────────┼────────────────┐
│             ▼                │
│          NK Node             │
│                              │
│     Dedicated GPU PC         │
│                              │
│   LLM Runtime / Models       │
└──────────────────────────────┘
```

NeuraKiln remains the primary interface.

NK Node provides the compute.

---

# Supported Runtime Stack

NK Node is built to manage the components used by NeuraKiln's local LLM stack, including:

- **llama.cpp**
- **llama-swap**
- **Strata**
- NeuraKiln model utilities and supporting runtime components

Backend availability may depend on your hardware and the version of NK Node installed.

---

# Model Switching

NK Node does not attempt to recreate NeuraKiln's chat or model-selection interface.

Model switching remains controlled from NeuraKiln.

NeuraKiln already supports selecting another model through **+ New Chat**, while `llama-swap` handles the underlying model lifecycle.

NK Node's responsibility is to keep the remote inference environment available and correctly configured.

---

# Automatic Pairing

NK Node is intended to remove the normal endpoint-configuration process from multi-PC inference.

When NeuraKiln and NK Node are available on the same supported network:

1. Open NK Node on the inference PC.
2. Open NeuraKiln on the primary PC.
3. Use the NK Node connection option inside NeuraKiln.
4. Complete pairing.
5. NeuraKiln and NK Node exchange the required connection information automatically.

You should not need to manually maintain endpoint URLs for normal NeuraKiln usage.

---

# Installation

## Requirements

NK Node is currently designed around:

- **Windows**
- **NVIDIA GPUs**
- A supported local network connection
- Sufficient VRAM/RAM/storage for the models you intend to run

Actual model requirements depend on the selected model, quantization, context length, and backend.

---

## Download

Download the latest NK Node release from the **Releases** section of this repository.

https://github.com/ToolshedMediaLab/NK-Node/releases/tag/NK-Node-v1.0.0

---

# First Launch

On first launch, NK Node will guide you through the available runtime and configuration options.

After setup, NK Node is designed to retain the configuration needed to restore the inference environment on later launches.

A normal dedicated-node workflow should therefore become:

```text
Boot PC
   ↓
Launch NK Node
   ↓
Restore inference environment
   ↓
Connect from NeuraKiln
```

Rather than rebuilding the server configuration every time.

---

# Updating Runtime Components

Local inference runtimes move quickly.

NK Node is designed to simplify updating supported components while preserving your existing configuration and model setup wherever possible.

Runtime updates should not require rebuilding your entire node from scratch.

---

# Models

NK Node does **not** require models to be bundled directly with the application.

You remain responsible for obtaining and using models according to their respective licenses and terms.

Model compatibility depends on the backend being used.

For llama.cpp-based inference, supported **GGUF** models can be used where compatible with the installed runtime.

---

# Multi-GPU Systems

NK Node is specifically useful for dedicated multi-GPU inference machines.

Actual performance depends on factors including:

- GPU architecture
- VRAM capacity
- PCIe topology
- Model architecture
- Quantization
- Context length
- Runtime
- GPU allocation
- Cache configuration

NK Node does not assume that every machine should use the same inference configuration.

---

# What NK Node Is Not

NK Node is **not**:

- A second NeuraKiln interface
- A replacement for NeuraKiln
- A chat frontend
- A cloud inference service
- A model hosting service operated by Toolshed Media Labs
- A requirement for using NeuraKiln on a single PC

If you run NeuraKiln and your models on the same machine, you may not need NK Node at all.

NK Node exists for users who want to separate the **interface/workstation** from the **inference hardware**.

---

# Network & Security

NK Node is intended for systems and networks you control.

Do not expose inference services directly to the public internet unless you understand and have independently secured the network configuration involved.

For normal use, NK Node should be operated on a trusted local network.

---

# NeuraKiln

NK Node is a companion project to **NeuraKiln**, the local AI suite from Toolshed Media Labs.

NeuraKiln provides the primary interface for local AI workloads, while NK Node allows supported workloads to use inference hardware installed in another PC.

**NeuraKiln:**  
https://github.com/ToolshedMediaLab/NeuraKiln

---

# Development Status

NK Node is actively developed alongside NeuraKiln.

Expect the supported runtime stack, hardware options, and integration capabilities to expand over time.

The current priority is reliable, low-friction remote **LLM inference**.

---

# Issues

If you encounter a reproducible NK Node problem, open a GitHub Issue with as much relevant information as possible.

Useful information includes:

- NK Node version
- NeuraKiln version
- Windows version
- GPU model(s)
- NVIDIA driver version
- Backend being used
- Model and quantization
- Relevant log output
- Steps required to reproduce the problem

Please remove passwords, API keys, private network credentials, and other sensitive information before posting logs publicly.

---

# License

See the repository's `LICENSE` file for current licensing terms.

Third-party runtimes, models, and dependencies remain subject to their own licenses.

---

## Toolshed Media Labs

NK Node is developed by **Toolshed Media Labs LLC** as part of the NeuraKiln ecosystem.
