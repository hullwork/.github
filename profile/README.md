<div align="center">
  <img src="./assets/hullwork-header.svg" width="100%" alt="Hullwork — open infrastructure for dependable AI agents" />
</div>

## Infrastructure for agents that do real work

Hullwork builds open, self-hosted infrastructure for AI agents that need to execute code and ship software—not just generate an answer.

> **An agent is dependable only when its execution boundary and delivery evidence are explicit.**

Our public projects cover the path from an agent request to a result you can trust:

`agent request` → **secure execution** → **verified deployment** → `observable result`

## Open-source projects

<div align="center">
  <a href="https://github.com/hullwork/sandbox">
    <img src="./assets/project-sandbox.svg" width="680" alt="Hullwork Sandbox — secure execution for AI agents" />
  </a>
</div>

### [Sandbox](https://github.com/hullwork/sandbox) — Secure execution for AI agents

Run an agent's shell and file operations inside a dedicated Kubernetes `gVisor` Pod. The self-hosted control plane manages durable workspaces, tenant-scoped credentials, quotas, checkpoints, and runtime lifecycle—without ever falling back to host execution.

**Interfaces:** Python SDK · CLI · MCP &nbsp; | &nbsp; **Proof:** [architecture](https://github.com/hullwork/sandbox#sandbox-platform) · [benchmarks](https://github.com/hullwork/sandbox/blob/main/docs/BENCHMARK_REPORT_2026-09-01.md) · [live project site](https://hullwork.github.io/sandbox/)

<div align="center">
  <a href="https://github.com/hullwork/site">
    <img src="./assets/project-site.svg" width="680" alt="Hullwork Site — verified website delivery for AI agents" />
  </a>
</div>

### [Site](https://github.com/hullwork/site) — Verified website delivery for AI agents

Turn an agent's deployment request into a real Kubernetes workload through HTTP, CLI, or MCP. The control plane handles tenancy, quotas, builds, ingress, observability, and scale-to-zero—then makes a real HTTP request and records the status code and body digest.

**Interfaces:** HTTP API · CLI · MCP &nbsp; | &nbsp; **Proof:** [architecture](https://github.com/hullwork/site#site) · [one-command demo](https://github.com/hullwork/site#see-the-proof-locally) · [live project site](https://hullwork.github.io/site/)

## What we optimize for

| Principle | Engineering consequence |
| --- | --- |
| **Boundaries over promises** | Untrusted code runs with explicit identity, resource, network, and runtime isolation. |
| **Evidence over status labels** | A deployment is successful only when the running address has been measured. |
| **Fail closed** | Missing control-plane or runtime dependencies never become permission to execute on the host. |
| **Composable interfaces** | HTTP APIs, CLIs, SDKs, and MCP tools keep products useful without hidden coupling. |
| **Operator ownership** | Workspaces, credentials, state, and deployment infrastructure stay in your environment. |

## Start with the boundary you need

- Need to execute agent-generated code safely? Start with **[Sandbox](https://github.com/hullwork/sandbox#one-command-to-see-the-point)**.
- Need to turn a generated site into a verified deployment? Start with **[Site](https://github.com/hullwork/site#see-the-proof-locally)**.
- Evaluating the architecture? Read each repository's explicit **known limitations** before adopting it.

<div align="center">
  <sub>Build the boundary. Measure the result.</sub>
</div>
