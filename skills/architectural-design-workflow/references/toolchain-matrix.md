# Architectural and interior-design toolchain

Use this matrix to route work by the artifact and level of fidelity the user needs. It is a capability guide, not a promise that every listed application is installed or connected. Before acting, verify the current application, license, plugin/MCP, and file-format path.

## Route by design stage

| Stage | Primary tools | Best suited to | Typical native / exchange artifacts | Keep in mind |
| --- | --- | --- | --- | --- |
| BIM authoring and coordination | Archicad, Revit, Vectorworks Architect | Information-rich building models, schedules, coordinated views, model-based documentation | PLN/PLA, RVT/RFA, VWX; IFC, BCF, DWG, PDF where supported | Preserve the chosen BIM application's native model as source of truth. IFC/DWG round-trips can lose application-specific data; verify critical elements after exchange. |
| CAD drafting and detail documentation | AutoCAD; compatible CAD tools | Dimensioned plans, details, schedules, annotations, 2D/3D CAD geometry | DWG, DXF, PDF | DXF is an exchange format and is not equivalent to a native DWG workflow. Verify units, layers, dimensions, external references, and round-trip behavior. |
| Fast architectural/interior modeling | SketchUp | Early massing, room layouts, furniture studies, client-facing editable spatial models | SKP; DWG/DXF or IFC when supported by the installed version/edition | Keep imported CAD geometry and approximate visual objects distinguishable; verify scale and axes. |
| NURBS and parametric design | Rhino + Grasshopper | Complex geometry, custom components, parametric options, façade/interior systems | 3DM, GH; DWG/DXF, STEP, OBJ and other supported exchange formats | Grasshopper definitions may depend on plugins and version-specific components. Record dependencies and bake/export only after checking geometry. |
| Detailed scene modeling and architectural visualization | Blender | Editable visualization geometry, furniture/detail modeling, materials, lighting, stills, animation | BLEND; FBX, OBJ, glTF/GLB and image/video outputs | A mesh/render scene is not automatically BIM or construction documentation. Use the architectural visualization workflow when this is the requested deliverable. |
| Real-time walkthrough and interactive review | Unreal Engine; Twinmotion | Immersive navigation, real-time lighting, client walkthroughs | UPROJECT; Datasmith, FBX or other supported scene exchange | Validate scale, orientation, material mapping, lighting, collision, and navigation after import. Treat this as a downstream presentation model. |
| Rendering within a design application | Enscape, Twinmotion, D5 Render, V-Ray | Rapid design review or production-quality stills/animation connected to a host model | Host-application project plus rendered images/video | Availability and interchange depend on the host application, plugin, license, and version. Verify them rather than assuming a direct link exists. |
| Graphic finishing and publication | Illustrator, InDesign; Folio for presentation layout | Vector cleanup, sheet graphics, editorial layout, presentation assembly | AI/INDD, PDF, SVG/PNG and Folio-supported outputs | Keep design generation and technical validation upstream. Folio remains the layout skill and is not absorbed into this skill. |

## Current workstation snapshot

Last inspected 2026-10-09. This is a snapshot; recheck before each task.

| Capability | Observed status | What can be claimed now |
| --- | --- | --- |
| AutoCAD | AutoCAD 2027 is installed. AutoCAD MCP Pro 1.6.0 is installed and registered in Codex for the `ezdxf` backend; isolated stdio initialization, architectural DXF template creation, save/reopen, and scope rejection were tested. Codex application restart is required to load the new MCP registration. | DXF drafting/inspection through the MCP after restart, limited to the configured workspace. It does not drive the live AutoCAD application on this Mac and does not provide DWG or 3D-solid support in this configuration. |
| Rhino | Rhino 8 is installed and was running. No Rhino/Grasshopper MCP was confirmed in the active Codex configuration. | Rhino is available as an application; direct Codex modeling control or a live Grasshopper connection is not yet verified. |
| SketchUp | SketchUp 2026 is installed in the workstation inventory. No SketchUp MCP/connector was confirmed. | Application availability only; direct automation and import/export behavior must be verified per task. |
| BIM | Archicad 29 is present in the workstation application inventory. No Archicad/Revit BIM connector was confirmed. Revit was not present in the inspected Mac application inventory. | Archicad application availability only; no BIM model automation or IFC coordination connector is confirmed. |
| Blender | Blender is installed and was running. The local `blender-skills:archviz` guidance is available; no Codex Blender MCP bridge was confirmed. | Blender can be used as an application if an appropriate local workflow is available. The skill by itself does not provide a live connector. |
| Visualization plug-ins / real-time | Enscape, Twinmotion, D5 Render, V-Ray, and Unreal Engine were not confirmed as installed or connected in the inspected inventory. | Treat as optional downstream targets; inspect the host application and current export/import path before promising a deliverable. |
| Graphic tools | Illustrator 2025 and InDesign 2025 are installed in the workstation inventory. Folio remains available as a separate skill. | Application availability does not establish direct automation; use Folio separately for presentation layout. |

## Connection-state vocabulary

Report the strongest state that has actually been observed:

1. **Not checked** — no recent environment inspection.
2. **Application detected** — installed or visible in the app inventory, but automation is not established.
3. **Connector configured** — MCP/plugin settings exist, but a current handshake has not succeeded.
4. **Connected** — the connector initialized and exposed its expected tools.
5. **Round-trip verified** — a representative artifact was created or opened, saved/exported, reopened, and checked for required properties.

Do not promote a tool to a higher state based on its marketing page, skill instructions, or successful startup alone.
