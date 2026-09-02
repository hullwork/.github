# Hullwork

A self-hosted agent platform, published as four products that are deployed
together and developed apart.

Each one builds, tests and releases on its own, and none imports another's
code. You can run any of them without the other three.

| | What it is | Reach for it when |
| --- | --- | --- |
| **[agent](https://github.com/hullwork/agent)** | Multi-agent runtime: ReAct loops, tool policy, human-in-the-loop approval, sub-agents, MCP connectors, durable scheduling, a Work UI and an OpenAI-compatible API | You want the agent runtime itself |
| **[sandbox](https://github.com/hullwork/sandbox)** | Kubernetes sandbox platform: gVisor-isolated workspaces with an HTTP API, a consumer SDK, an MCP bridge and an operator console | You need to run untrusted code with an isolation boundary you can point at |
| **[site](https://github.com/hullwork/site)** | Website deployment control plane: build, deploy, version, roll back, scale to zero | You need generated sites to become real, addressable deployments |
| **[infra](https://github.com/hullwork/infra)** | Controller-free GitOps package compiler | You want deployments described as data and compiled, not templated by hand |
| **[platform-composition](https://github.com/hullwork/platform-composition)** | The composition: which packages, which versions, which cluster | You are deploying more than one of the above |

## Where to start

**To understand the whole thing** — read
[`platform-composition/docs/architecture.md`](https://github.com/hullwork/platform-composition/blob/main/docs/architecture.md).
It is the only document that describes all four together: what each one is,
where the boundaries between them are, and what crosses them.

**To run something** — each repository's README opens with a quick start that
was executed as written. Where a command could not be verified, the README
says so instead of implying it works.

**To deploy this for a company** — read
[`platform-composition/docs/private-deployment.md`](https://github.com/hullwork/platform-composition/blob/main/docs/private-deployment.md):
capacity, cluster prerequisites, the full secret inventory, the multi-tenancy
model, and an example configuration you can copy.

## Boundaries worth knowing before you deploy

These are the parts that are easy to get wrong, and the reason the split is
worth the extra repositories.

**Agent is an external tenant of Sandbox and of Site.** Not a sibling
component — the trust boundary is the one you would draw around a third party.
Both control planes authenticate Agent's credential and scope everything to
the tenant it names. Agent cannot declare an identity in a request body; a
caller-declared identity is rejected rather than ignored.

**Each product owns its own state.** Three PostgreSQL instances, not one
shared schema. Two object storage planes with separate credentials. A
credential for one cannot reach the other.

**Infra never knows what it is deploying.** It is a pure function: four
schema-validated records in, an Argo `ApplicationSet` stream out. It does not
reach the network, read environment variables, or touch a cluster. Adding a
product takes three data files and no compiler change.

## On the published history

Each repository starts from a single initial commit. The development history
that preceded it was internal — most of its commit messages were written in
Chinese, and early commits carried cloud resource identifiers that were
replaced with placeholders later but stayed reachable through the commits that
introduced them. Squashing removes all of that at once rather than leaving a
rewrite that has to be trusted.

The trees themselves are unchanged: they are exactly what that history built
up to, reviewed and tested.
