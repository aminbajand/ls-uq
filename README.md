# LS-UQ — Supplementary Material

Supplementary material for the paper *"A Cross-Layered Standard for Credibility Activities in Simulation-Based Engineering"*. This repository provides extended XML listings, system model diagrams, simulation results, tool demonstration videos, and schema specification documents that complement the paper.

## Repository Structure

```
├── figures/                     Paper figures (standalone PDFs)
│   ├── document-skeleton.pdf      LS-UQ schema document skeleton
│   ├── activity-chain.pdf         Credibility activities as typed schema elements
│   ├── domain-hierarchy.pdf       Operational domain hierarchy with coverage
│   ├── integration-arch.pdf       Integration architecture (supplementary)
│   └── integration-scenarios.pdf  Adoption scenarios (supplementary)
│
├── specifications/              Schema specification documents
│   ├── ls-uq-base-schema-v1.pdf   Base LS-UQ schema (prior version)
│   ├── ls-uq-extension-proposal-v2.pdf  Extended schema proposal (this paper)
│   └── *.svg                      Architecture and workflow diagrams
│
├── use-cases/                   Industrial use case artifacts
│   ├── dc-motor/                  Credible DC Motor Model
│   │   ├── dc_motor.xml             Main LS-UQ file (verification + forward UQ)
│   │   ├── dc_motor_parameters.xml  Uncertain parameter definitions (R, L)
│   │   ├── dc_motor_axes.xml        Operational domain axes (voltage, torque)
│   │   ├── dc_motor_boundary.xml    Domain boundaries (HyperRectangle)
│   │   ├── dc_motor_units.xml       Unit definitions
│   │   └── *.png, *.pdf             System diagrams and simulation results
│   │
│   └── aerospace/                 Aerospace Multi-Stakeholder Validation
│       ├── ecs/                     Environmental Control System sub-model
│       │   ├── ecs.xml                Validation activity with ConvexHull boundary
│       │   ├── ecs_axes.xml           Operational domain axes (altitude, Mach)
│       │   └── ecs_boundary.xml       Domain boundaries
│       ├── mobile-valve/            Hydraulic valve component model
│       │   └── mobile_valve.xml       Forward UQ (11-dimensional operational domain)
│       └── *.png                    System architecture diagrams
│
└── tool-support/                Tool demonstrations
    ├── dymola/                    Dymola integration
    │   ├── dymola-integration-screenshot.png
    │   ├── dymola-lsuq-example.png
    │   └── dc-motor-dymola-demo.mp4
    └── lsuqviz/                   LSUQViz visualization tool
        ├── lsuqviz-singleplot-2d-screenshot.png
        ├── lsuqviz-singleplot-2d-video.mp4
        ├── lsuqviz-doubleplot-2d-screenshot.png
        └── lsuqviz-doubleplot-2d-video.mp4
```

## Paper-to-Repository Mapping

The table below maps each supplementary reference in the paper to the corresponding files in this repository.

| Paper Reference | Files |
|---|---|
| Additional system model diagrams (DC motor) | `use-cases/dc-motor/system-model-L3-causal.png` |
| Axis and boundary XML definitions (DC motor) | `use-cases/dc-motor/dc_motor_axes.xml`, `dc_motor_boundary.xml` |
| Verification test specifications and reference solutions | `use-cases/dc-motor/dc_motor.xml` (Verification elements), `verification-*.pdf` |
| Forward UQ parameter set and results | `use-cases/dc-motor/dc_motor_parameters.xml`, `forward-uq-pdf-result.pdf` |
| ECS validation results | `use-cases/aerospace/ecs/ecs.xml` |
| Valve model operational domain and UQ domain | `use-cases/aerospace/mobile-valve/mobile_valve.xml` |
| Tool screenshots and demonstration videos | `tool-support/dymola/`, `tool-support/lsuqviz/` |

## Paper Figures

The `figures/` directory contains standalone PDFs of the approach diagrams, compiled from TikZ source. These are the same diagrams that appear in the paper, provided here for full-resolution viewing.

| File | Description |
|---|---|
| `document-skeleton.pdf` | Overall document skeleton of the LS-UQ extension schema |
| `activity-chain.pdf` | Credibility activities as typed schema elements with CSP phase annotations |
| `domain-hierarchy.pdf` | Operational domain hierarchy (ODD, OD, Model OD) with coverage classifications |
| `integration-arch.pdf` | Integration architecture: LS-UQ schema imports and SSP Traceability references |
| `integration-scenarios.pdf` | Three adoption scenarios (Standalone, LS-UQ First, Traceability First) |

## Schema Specifications

The `specifications/` directory contains the schema specification documents:

- **`ls-uq-base-schema-v1.pdf`** -- The base LS-UQ schema specification (prior version), defining the core XML types for uncertainty quantification data exchange within the SSP/FMI ecosystem.
- **`ls-uq-extension-proposal-v2.pdf`** -- The extended schema proposal (this paper's contribution), describing the new schema elements: the three-level domain hierarchy, activity types, assumptions framework, and SSP LS Traceability integration.
- **`*.svg`** -- Architectural diagrams including the activity workflow, domain hierarchy, and SSP Traceability integration scenarios.

## Use Cases

### DC Motor

A single-stakeholder credibility workflow for a Modelica-based DC motor model. Exercises modeling assumptions, deterministic and stochastic verification, and forward uncertainty quantification within a single Credible Modeling Process (CMP).

**XML files:**

| File | Description |
|---|---|
| `dc_motor.xml` | Main LS-UQ file containing two verification activities (deterministic and stochastic) and a forward UQ activity with 256 Latin Hypercube samples |
| `dc_motor_parameters.xml` | Parameter definitions: resistance R ~ Normal(0.1, 0.01) Ohm, inductance L ~ Uniform[0.105, 0.115] mH, plus 4 deterministic parameters |
| `dc_motor_axes.xml` | Operational domain axes: voltage (V) and torque (T) |
| `dc_motor_boundary.xml` | HyperRectangle domain boundaries |
| `dc_motor_units.xml` | Unit definitions for the model parameters |

**Figures:**

| File | Description | In paper? |
|---|---|---|
| `system-topology-L2.png` | System topology (SmartSE Level 2) | Yes |
| `system-model-L3-acausal.png` | Acausal simulation topology (Level 3) | Yes |
| `system-model-L3-causal.png` | Causal simulation view in Dymola (Level 3) | Supplementary only |
| `system-model-L4-fmu.png` | FMU component architecture (Level 4) | Yes |
| `operational-domains.pdf` | Operational domain hierarchy with activity domains | Yes |
| `verification-deterministic.pdf` | Deterministic verification: single-trajectory time response | Supplementary only |
| `verification-stochastic.pdf` | Stochastic verification: average trajectory with tolerance band | Yes |
| `verification-cdf.pdf` | Stochastic verification: CDF of steady-state motor speed | Yes |
| `forward-uq-pdf-result.pdf` | Forward UQ result: PDF of steady-state idle speed | Supplementary only |
| `uncertain-param-distributions.png` | Input uncertain parameter distributions (R, L) | Supplementary only |

### Aerospace

A multi-stakeholder validation scenario for an aircraft vehicle systems composite model. An OEM integrator and a Tier 1 supplier exchange credibility evidence across organizational boundaries.

**ECS sub-model** (`ecs/`): Environmental Control System validation activity with ConvexHull boundary in the altitude-Mach plane, two experiment points, and relative error metrics for outlet and inlet temperatures.

**Mobile valve** (`mobile-valve/`): Hydraulic valve component model with forward UQ across an 11-dimensional operational domain (control signals and pressures), 6 experiment points, and 6 observed flow/pressure variables.

**Figures:**

| File | Description | In paper? |
|---|---|---|
| `aircraft-vehicle-systems.png` | Aircraft vehicle systems composite model architecture in easySSP | Yes |
| `acvs-easyssp.png` | Alternative easySSP view of the aircraft composite model | Supplementary only |
| `lsuqviz-aerospace-alt-mach.png` | LSUQViz visualization of the ECS model ConvexHull boundary in the altitude-Mach plane | Yes |

## Tool Support

### Dymola

- **`dymola-integration-screenshot.png`** -- Screenshot showing the Dymola integration with LS-UQ for the DC motor use case
- **`dymola-lsuq-example.png`** -- Dymola LS-UQ example configuration screenshot
- **`dc-motor-dymola-demo.mp4`** -- Video demonstration of the Dymola export/import workflow: configuring input uncertainties, running Monte Carlo experiments, and exporting the SSP archive with LS-UQ metadata

### LSUQViz

- **`lsuqviz-singleplot-2d-screenshot.png`** -- Single-plot 2D visualization of operational domain boundaries
- **`lsuqviz-singleplot-2d-video.mp4`** -- Video demonstration of single-plot domain exploration
- **`lsuqviz-doubleplot-2d-screenshot.png`** -- Double-plot 2D visualization comparing domain boundaries with simulation trajectory classification
- **`lsuqviz-doubleplot-2d-video.mp4`** -- Video demonstration of dynamic simulation point classification against domain boundaries

## Reading the XML Files

All XML files conform to the LS-UQ schema with namespace `http://openscaling.org/UQ1/UncertaintyQuantification`. They also reference SSP and SSP Traceability namespaces. The files are human-readable and can be opened in any text editor or XML viewer. Key element types to look for:

- `<uq:Verification>` -- Verification activities with reference data and error metrics
- `<uq:ForwardUncertaintyQuantification>` -- Forward UQ with parameter sets and sampling methods
- `<uq:Validation>` -- Validation activities with experiment points and observed variables
- `<uq:OperationalDomain>` -- Operational domain boundaries (ConvexHull or HyperRectangle)
- `<uq:Assumption>` -- Modeling assumptions constraining the model scope
