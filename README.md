# Electronic Systems Engineering: SysML Model

SysML model of the xCPS production line, built for the TU/e design-based-learning project
in Electronic Systems Engineering (course 5XIC0). This repository holds the SysML part of
the project. The same system was also captured as an executable POOSL model and evaluated
with Python and C scripts, kept in the sibling repositories linked below.

The model was built in Eclipse Papyrus using the SysML 1.6 profile. It describes the xCPS
assembly line from several viewpoints: what the machine has to do (requirements and use
cases), how it is built (block and structure diagrams), what flows through it (value and
flow types), how it behaves (activity diagrams for the control logic), and how design
choices map to money (a parametric revenue analysis). The revenue analysis captures the
same cost, price, volume and profit relations that the design-space scripts evaluate, so
the SysML model and the scripts describe the same trade-off in two forms.

## What the model covers

The model is organized into the standard SysML pillars:

- Requirements. Top-level requirements grouped by theme: functional requirements, batch
  processing capability, collision avoidance and safe operation of specific stations
  (belt 5, index table 2), performance evaluation, and cost and time-to-market.
- Structure. A top block, `xCPS`, decomposed into an I/O Module and a Manufacturing Module.
  Blocks model the physical stations: belt, index table, pick and place, stopper, switch,
  turner, loading table and optical sensor. Slow, normal and fast variants of the belt,
  gantry and table capture the design alternatives that differ in speed and cost.
- Value and flow types. The items that move through the line: tokens, products, top and
  bottom pieces, the inverted top, and their type definitions.
- Behaviour. Use cases from the operator's viewpoint, and activity diagrams for the control
  logic. The dispatcher activity drives loading of the inverted top and bottom, the turner
  and index-table steps, assembly, and storing of the finished product, with the sensor
  wait and pass steps that sequence a piece along the belts.
- Revenue analysis. A parametric view relating bill-of-materials cost, price, sales volume,
  engineering-change delay and profit, matching the financial model used in the scripts.

## Diagrams

The Papyrus model contains these diagrams:

| Diagram | Kind | Subject |
| --- | --- | --- |
| xCPS overview | Package | Top-level package structure of the model. |
| xCPS_Machine model overview | Package | Model organization by SysML viewpoint. |
| xCPS_Machine Operation | Use case | Operator interaction with the machine. |
| xCPS_Machine Top-Composition | Block definition | Decomposition of the system into modules. |
| Structure components | Package | The component blocks of the line. |
| I/O Module | Block definition | Composition of the input and output module. |
| Manufacturing Module | Block definition | Composition of the manufacturing module. |
| Value_types | Block definition | Value and flow type library. |
| Requirements | Requirements | Top-level requirements. |
| Behaviours | Package | Organization of the behavioural diagrams. |
| dispatcher | Activity | Dispatch and assembly control logic. |
| xCPS revenue analysis | Parametric | Cost, price, volume and profit relations. |

## Contents

| Path | Role |
| --- | --- |
| `xCPS/xCPS.uml` | The SysML model: requirements, blocks, ports, value types, activities and the parametric constraints. |
| `xCPS/xCPS.notation` | Papyrus diagram notation (layout and appearance of every diagram listed above). |
| `xCPS/xCPS.di` | Papyrus diagram index tying the model to the SysML 1.6 architecture. |
| `xCPS/xCPS_en_US.properties` | Element display names. |
| `xCPS.zip` | Packaged copy of the seven core model files. |
| `.metadata/` | Eclipse workspace metadata for the project. |
| `pull`, `push` | Small git helper scripts used while working on the model. |

## Opening the model

The model opens in Eclipse Papyrus with the SysML 1.6 architecture. Import the project into
an Eclipse workspace, then open `xCPS/xCPS.di` to load the diagrams. The `.uml`, `.notation`
and `.di` files belong together and are read by Papyrus, not by hand. GitHub reports the
repository language as D because of the `.di` file extension; the files are Papyrus SysML,
not D source.

## Related repositories

This is one part of the Electronic Systems Engineering design-based-learning project. The
other parts:

- [tue-electronic-system-engineering-poosl](https://github.com/danieltyukov/tue-electronic-system-engineering-poosl): executable POOSL performance model of the same system.
- [tue-electronic-system-engineering-script](https://github.com/danieltyukov/tue-electronic-system-engineering-script): Python and C scripts for the design-space and profit analysis.

## Technologies

- SysML 1.6
- Eclipse Papyrus
