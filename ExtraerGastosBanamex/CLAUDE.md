# UiPath Project: ExtraerGastosBanamex

This is a UiPath automation project. When working on this project, use the appropriate
UiPath skill rather than editing project files directly — the skills understand UiPath
file formats, project conventions, and the `uip` CLI, and will keep the project valid.

## Which skill to use

- **uipath-rpa** — `.xaml` and coded (`.cs`) workflows, UI automation, Object Repository selectors, test cases. The default for most work in this project.
- **uipath-agents** — coded (Python: LangGraph / LlamaIndex / OpenAI) and low-code (`agent.json`) agents.
- **uipath-maestro-flow** — `.flow` Maestro orchestration files.
- **uipath-maestro-bpmn** — `.bpmn` process orchestration.
- **uipath-maestro-case** — case management plans.
- **uipath-coded-apps** — coded web and action apps (`app.config.json`, `action-schema.json`).
- **uipath-api-workflow** — JSON API workflows run by `uip api-workflow run`.
- **uipath-data-fabric** — Data Fabric entities and record CRUD.
- **uipath-human-in-the-loop** — authoring approval / validation / Human Task nodes.
- **uipath-solution** — `.uipx` solutions, SDD/PDD authoring, packaging and publishing.
- **uipath-platform** — Orchestrator, Studio Web, Integration Service, and LLM Gateway operations.
- **uipath-test** — Test Manager projects, cases, and executions.
- **uipath-review** — read-only audit of project structure and best practices.
- **uipath-troubleshoot** — diagnosing failures, errors, and regressions.

If you are unsure where to start, use **uipath-planner** to break the request into tasks
and route each to the right skill.

## ⚠️ Where this actually runs in Orchestrator (read before deploying)

**This process does NOT show up under the "Solutions" tab in Orchestrator.** It was deployed
directly (folder + process binding via `uip or` commands), not via `solution deploy run`, so
there is no tracked "Solution Deployment" record for the live version.

- **Live folder:** `ExtraerGastosBanamex` (tenant root, restricted — not under `Shared`, not
  under Personal Workspace).
- **Access:** only `ricardo.rosales@uipath.com` (Folder Administrator) and the
  `RobotUnattended` robot account (Automation User). No org-wide groups have access.
- **Machine:** `UnAttendedMachine` (already connected, shared org infra).
- **Credential:** Orchestrator Credential Asset `BancaNetBanamex` (Global scope, Automations
  only), created *inside that folder* — the workflow reads it via `GetRobotCredential`, not
  from local Windows Credential Manager.
- **Trigger:** `ExtraerGastosBanamex-Diario`, daily 8am `Central Standard Time (Mexico)` —
  created **disabled**; enable it in Orchestrator → that folder → Triggers when ready.
- **Old/inactive entries you may see and should ignore:**
  - `Solutions → Deployments → ExtraerGastosBanamex-Shared` (folder `Shared`) — uninstalled on
    2026-09-08, superseded by the root folder above.
  - `My Workspace/ExtraerGastosBanamex` — still Process v1.0.0, uses the old local Windows
    Credential Manager path (`GetSecureCredential`), **not** the current credential-asset
    fix. Fine for quick manual/attended testing, but not the source of truth for production.

If you need to find "where does this really run," go straight to **Orchestrator → Folders →
ExtraerGastosBanamex** (root level) — not the Solutions tab.
