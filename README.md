# myskills

This repository is a small skill library for agent workflows around draw.io/diagrams.net output.

It is not an application or package. The repo currently contains prompt-based skills, supporting reference material, and examples that help an agent generate higher-quality `.drawio` XML files for architecture and process diagrams.

## What is in this repo

### `drawio-diagrams-enhanced/`

A broader draw.io skill for general-purpose diagram generation with extra support for project-management and business artifacts.

It covers:
- flowcharts
- swimlane diagrams
- BPMN and UML
- network and system diagrams
- org charts
- WBS, RACI, Gantt, risk matrices, and related PMBOK-style visuals

This directory also includes a `reference/` folder with prompt templates, examples, and quick-reference material for common diagram types.

## Repository layout

```text
.
├── README.md
└── drawio-diagrams-enhanced/
    ├── SKILL.md
    └── reference/
        ├── bir-tax-compliance-workflow.md
        ├── drawio-shape-reference.md
        ├── insightpulse-architecture.md
        ├── pmp-formulas-reference.md
        ├── project-charter-template.md
        ├── project-wbs-odoo-implementation.md
        └── raci-matrix-template.md
```

## When to use this repo

Use `drawio-diagrams-enhanced` when:
- the user asks for any kind of draw.io diagram
- the diagram is process-heavy, business-heavy, or PM-heavy
- you want examples, templates, or broader shape guidance

## Sample prompts

### Architecture onboarding prompt

Use a prompt like this when you want an agent to inspect a codebase and produce a high-level draw.io diagram for onboarding:

```text
Act as a software architecture engineer. Analyze this project and create a draw.io diagram for onboarding.

Focus on the main entry points, the backbone of the system, and the major internal flows. Use CoreDNS as the example target project.

Do not go deep on every dependency, package, or external integration. Keep the diagram at a level that helps a new engineer understand:
- where execution starts
- the main components
- how requests or control flow move through the project
- the major boundaries in the system

Save the result as a `.drawio` file in canonical style.

Use the `drawio-diagrams-enhanced` skill and generate it as a `Flowchart` unless another diagram type below is a better fit.
```

### Diagram type variants

You can reuse the same prompt and only change the requested diagram type:

#### Standard diagram types

- `Flowcharts` for basic architecture flow, request flow, or decision flow
- `Cross-Functional Flowcharts (CFF)` for swimlane-style ownership across teams or modules
- `BPMN Diagrams` for business process workflows
- `UML Diagrams` for class, sequence, or use-case views
- `Network Diagrams` for infrastructure, cloud, or system topology
- `Org Charts` for team or ownership structure
- `Mind Maps` for exploratory system mapping
- `Entity Relationship Diagrams` for schema and data relationships

#### PMP/PMBOK project management diagrams

- `Work Breakdown Structure (WBS)` for project decomposition
- `Project Network Diagrams` for PERT, CPM, and task dependencies
- `Gantt Charts` for schedules and milestones
- `RACI Matrices` for responsibility mapping
- `Risk Register Diagrams` for probability-impact views
- `Stakeholder Maps` for power-interest mapping
- `Resource Histograms` for capacity and allocation
- `Communication Plans` for reporting and information flow
- `Process Group Diagrams` for initiation through closing
- `Knowledge Area Maps` for PMBOK knowledge-area coverage

### Short prompt template

For quick reuse:

```text
Analyze this repository and create a `.drawio` diagram in canonical style using the `drawio-diagrams-enhanced` skill as a `[DIAGRAM TYPE]`.

Focus on the main entry points, core modules, and major flows only. Do not expand every dependency or external service. The goal is fast onboarding for a new engineer.
```

## How to maintain this repo

If you add more skills, keep each one self-contained:
- put the main instructions in `SKILL.md`
- add only the references that materially improve output quality
- prefer concrete examples over long theory
- keep reusable templates in a nearby `reference/` directory

If you update an existing skill:
- keep trigger guidance clear
- keep output requirements explicit
- include quality checklists where failure modes are common
- avoid duplicating the same guidance across multiple files unless it is intentional

## Intended use

This repo makes the most sense as source material for a local skill system such as Codex/Claude-style skill directories. In practice, that means the directories here are meant to be copied, installed, or referenced by whatever agent environment loads `SKILL.md` files.
