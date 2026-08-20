# Mission 05 — The Driver Rift

## Briefing
PHX-07 finally has a GPU workload, but the application reports that no usable accelerator exists even though the hardware is physically present.

## Objective
Understand the layered GPU software path: PCIe device → kernel driver → NVIDIA userspace libraries → CUDA runtime → container runtime → application.

## Safety rule
Do not intentionally uninstall or corrupt the working NVIDIA driver on your primary laptop. Use observation, containers, a VM where GPU passthrough is appropriate, or a controlled version-mismatch exercise that cannot strand the host.

## Build
Record `lspci` visibility, loaded modules, `nvidia-smi`, driver version, CUDA/runtime information, and a minimal GPU test where supported.

## Deliberate failure
Use a controlled mismatch such as a container without GPU exposure, an intentionally wrong runtime configuration, or a test program targeting an unavailable capability.

## Investigation
Ask at each layer: is the device visible, is the kernel driver attached, can management tooling communicate, can the runtime enumerate the GPU, can the application use it?

## Evidence to save
- GPU software-stack diagram
- healthy and failed enumeration results
- exact layer where visibility stops

## Victory condition
You can explain why “CUDA failed” is too vague and identify the precise boundary that failed.
