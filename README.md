# Agentics Azure Sandbox smoke assembly line

This public ALP fixture proves the complete execution path without spending a
real model token:

1. import the repository into Agentics;
2. dispatch its kickoff task;
3. let the managed runner create one Azure Container Apps Sandbox;
4. start Docker and the repository devcontainer inside that Sandbox;
5. run real Claude Code and Vibecast against the repository-owned deterministic
   Anthropic scenario;
6. create and commit `RESULT.md`;
7. settle the Agentics task successfully and delete the Sandbox.

The model scenario is stored at
`.agentics/testbench/scenarios/azure-sandbox-hello-world.json`. The deployed
Sandbox controller content-addresses and registers it for only the dispatched
job, so ordinary assembly lines continue to use their configured model provider.
