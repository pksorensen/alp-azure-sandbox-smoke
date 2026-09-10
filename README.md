# Azure Sandbox smoke assembly line

Import this directory as an Agentics assembly line. It has three sequential
stations — Plan, Build, and Verify — and remains intentionally small enough for
the deterministic Claude gateway emulator.

The model fixture lives beside the line under
`.agentics/testbench/scenarios/azure-sandbox-hello-world.json`. Importing the
line carries that fixture into each dispatched Job; a simulation-enabled runner
registers it with its gateway and selects it only for that Job.

Each station deliberately takes several visible steps: it checks the Vibecast
MCP session, inspects its job and Git workspace, creates and reads a committed
proof file, publishes a delivery artifact to Agentics, and finally calls the
Vibecast `stop_broadcast` MCP tool.

Acceptance requires all of the following:

1. the Azure controller discovers or receives the project;
2. a Sandbox is created for the station job;
3. Docker and the devcontainer start inside the Sandbox;
4. the runner reaches the configured gateway and completes all three jobs;
5. `RESULT.md` is committed with the expected content;
6. the Sandbox is deleted after completion.
