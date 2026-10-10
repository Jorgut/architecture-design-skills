---
name: architectural-design-workflow
description: 建筑与室内设计工作流，支持空间分析、BIM/CAD图纸、参数化与3D建模、建筑可视化；适用于方案研究、模型协同、图纸审查和空间表达。
---

# Architectural & Interior Design

Coordinate architectural and interior work from brief and spatial analysis through technical drawings, design diagrams, concept imagery, 3D modeling, and presentation handoff. Select only the phases needed for the requested deliverable.

## Boundaries

- Distinguish user-provided facts, measured/source geometry, assumptions, estimates, and verified regulations. Never present an estimate as a code requirement.
- Do not invent site dimensions, door positions, clearances, structure, services, accessibility provisions, or approval status.
- Keep concept images, schematic diagrams, measured drawings, permit documents, and construction documents clearly distinguished. An image or schematic is not evidence of code compliance or buildability.
- Before promising a file format, inspect available apps, libraries, connectors, and permissions. DWG authoring/export needs a compatible CAD application or converter; never label SVG or DXF as DWG.
- External skills and generation tools are optional capabilities. Do not copy external skill files or claim a tool was run when it was unavailable.
- Keep presentation layout in Folio. This skill prepares and checks design content; it does not replace or modify Folio's layout rules.

## Independent specialist skills

The unified workflow coordinates work; it does not absorb the detailed procedures of specialist skills. Install the three sibling skills from this repository together when you want both direct invocation and coordinated routing.

- For area, capacity, ratios, parking, or space-program calculations, use `$space-program` and its references. Its sibling source is `../space-program/SKILL.md`.
- For architectural/interior/landscape concept-image prompts and image-edit constraints, use `$arch-prompt` and its references. Its sibling source is `../arch-prompt/SKILL.md`.
- Keep this skill responsible for the overall brief, selecting and sequencing design phases, CAD/diagram/model handoffs, consistency checks, and delivery boundaries.

If a specialist skill is not installed or discoverable in the current environment, state that limitation and use only the relevant bounded guidance in this coordinator; do not claim that the specialist skill ran.

## Choose a work mode

| User goal | Mode |
| --- | --- |
| Area, capacity, ratios, parking, or space brief | Spatial program and analysis |
| Existing CAD/DWG drawing review or new technical drawing | CAD drafting and drawing QA |
| Adjacency, zoning, circulation, operations, or concept explanation | Design diagrams |
| Design direction or image prompt | Concept visualization |
| Editable 3D massing/model or spatial render | 3D modeling and visualization |
| Client-facing deck | Prepare content and assets, then use Folio separately |

Do not force every task through the full workflow. Identify the required accuracy, source data, editable format, and intended use first.

## 1. Establish the brief

Collect only inputs that can change the outcome: project type and use, location, stage, audience, site/floor area, source drawings, known dimensions and units, operating patterns, budget, constraints, required views/files, and reference material. Ask concise questions for high-impact unknowns. If proceeding without an input, record the assumption and its effect.

## 2. Spatial program and analysis

For calculations and program comparisons:

1. Identify each quantity, unit, and measurement basis, including the denominator for ratios.
2. Classify inputs as user data, authoritative document, explicit assumption, or non-regulatory benchmark.
3. Show formulas and enough arithmetic to reproduce results. For uncertain inputs, show a reasonable range or sensitivity case.
4. Verify current local requirements from applicable official sources before making a compliance claim. If jurisdiction or standard is unknown, state that compliance cannot be determined.
5. Report conclusions alongside source, basis, assumptions, and unresolved items.

For detailed formulas and benchmark references, route to the independent `$space-program` skill and its linked references; its sibling source is [space-program/SKILL.md](../space-program/SKILL.md).

## 3. CAD/DWG drafting and drawing QA

For an existing drawing, first identify file type, units, scale, coordinate origin, drawing status, layers, references, and what the user wants checked. Preserve source geometry; do not silently redraw or overwrite it. Report geometry, dimension, annotation, layer, and coordination issues separately from code-compliance issues.

For new drawings, establish the drawing purpose and level of detail before drafting. Use confirmed dimensions and geometry as the source of truth. Keep units, scale, coordinates, layer names, lineweights, text, dimensions, and title/status consistent throughout the file. Include only details supported by the brief or source documents.

Before exporting, check key dimensions, closed/open boundaries as appropriate, openings and door swings, room labels, furniture clearance, circulation endpoints, and references. Reopen or round-trip the exported file in a compatible viewer when available.

- If a compatible CAD tool can create/edit DWG, use it and validate the saved file.
- If DWG tooling is unavailable but DXF creation and validation are supported, offer DXF as an editable fallback and label the format accurately.
- If only vector/page tools are available, create a clearly identified SVG or PDF schematic; do not imply it is a DWG or a construction drawing.
- Do not assert permit or construction readiness without the required project information and professional/regulatory review.

## 4. Diagrams and analytical drawing

Translate the program into relationships before drawing: users, activities, adjacency, arrival, service sequence, public/private zones, sightlines, and key spatial experience. Choose a diagram form suited to the question:

- Use a scaled plan only when reliable dimensions or source CAD geometry are available.
- Use a not-to-scale vector diagram for conceptual zoning or circulation when dimensions are missing; label it accordingly.
- Use flowchart tools such as FigJam/Mermaid for abstract sequences, decisions, or service logic. Do not use abstract flowchart layout as a substitute for a physical floor plan.
- Use image generation for atmosphere or concept exploration, never as authoritative technical geometry.

For plan diagrams, check that boundaries, openings, door assumptions, furniture, service points, labels, and route endpoints agree. Separate operationally distinct flows (for example guests and staff); do not route lines through walls or imply an unshown opening. State what the diagram explains and what remains unverified.

## 5. Concept visualization and image prompts

Translate the spatial program into design priorities before choosing a style. Structure prompts around project intent, spatial relationships, fixed geometry, materials, context, light, camera, image ratio, intended use, and exclusions. For image edits, name what may change and what must remain fixed. Produce one primary prompt and up to two variants only when useful; use only parameters confirmed for the selected image tool.

For specialist vocabulary and tool-specific syntax, route to the independent `$arch-prompt` skill and its linked references; its sibling source is [arch-prompt/SKILL.md](../arch-prompt/SKILL.md). Do not describe generated images as measured or buildable evidence.

## 6. 3D model building and visualization

First classify the requested model: concept massing, spatial study, design-development model, visualization mesh, or dimensionally coordinated model. Confirm source geometry, units, scale, required detail, editable format, and intended downstream use.

- Build from reliable plans/elevations or confirmed dimensions when accuracy matters. Block out major volumes and openings first; check them before adding furniture, details, materials, and lighting.
- Keep model structure understandable: organize major building elements, furniture, site/context, and cameras into named groups/collections where the tool supports them.
- Separate modeled geometry from visual placeholders and state the modeling tolerance or known limitations.
- A single-image-to-3D conversion may create a visual mesh, but cannot reliably infer hidden geometry, dimensions, construction, or code compliance. Treat it as a concept asset.
- For architectural stills, confirm scale and camera before detailed materials and lighting. If Blender and the external `archviz` skill are available, route rendering guidance to it; otherwise create a model brief or use the available modeling tool without claiming a Blender scene was produced.
- Before delivery, verify the native project or exported mesh opens, the stated format is correct, and key scale/orientation assumptions are documented.
- For an editable Blender scene, iterative render review, camera tour/storyboard, or optional Blender-to-Unreal walkthrough, follow [references/architectural-visualization.md](references/architectural-visualization.md). Keep visualization quality checks distinct from CAD and construction-document checks.

## Tool capability check

At the start of a file-generation task, determine which relevant capabilities are actually available. Distinguish an installed application, a configured connector, a successful live connection, and a verified file round-trip; these are separate capability levels. An application being installed does not mean Codex can drive it, and an MCP being configured does not prove a tool call works.

Use [references/toolchain-matrix.md](references/toolchain-matrix.md) to select a tool by design stage, accuracy, editable source format, and exchange needs, and to see the last inspected workstation status. Recheck current availability for each task because installations, licenses, plugins, and MCP connections can change. For example, a Mermaid/FigJam generator can create abstract flow diagrams but not dimensionally accurate plans; an image-to-3D service can produce a mesh from a URL but not a coordinated architectural model. State unavailable formats or fidelity limits before choosing a fallback.

## Handoff and quality check

Before delivery, confirm that:

- calculations use consistent units and expose their basis;
- drawing geometry, dimensions, labels, and analysis diagrams agree with source information;
- concept prompts, diagrams, CAD files, and 3D model do not contradict one another;
- assumptions and regulatory verification status are visible;
- each artifact is labeled as concept, schematic, measured, or coordinated at the appropriate level;
- exported files open in a compatible viewer when that check is available;
- limitations are stated plainly.

For a presentation, hand off approved content and assets to Folio as a separate step.
