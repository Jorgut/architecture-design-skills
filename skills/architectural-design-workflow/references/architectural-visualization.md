# Architectural visualization workflow

Use this workflow when the deliverable is an editable architectural/interior scene, still renders, a camera tour, or a real-time walkthrough. It is informed by [OpenAI's architectural visualization case study with Astra](https://developers.openai.com/blog/architectural-visualization-with-astra), then adapted as a reusable workflow rather than a project-specific recipe.

## Keep the model and the image connected

- Treat the native scene as the editable source of truth. Prefer building and revising geometry through the target application's API (for Blender, `bpy`) over generating a flattened image when the user asks for a model or multiple views.
- Start from the brief and any approved plan, elevations, dimensions, and references. Distinguish measured geometry from inferred or illustrative geometry; do not let an attractive render silently change confirmed dimensions or circulation.
- Keep architectural elements, openings, furniture, site/context, materials, lights, and cameras organized so later revisions can target a coherent part of the scene.
- Save a versioned backup before substantial redesigns or engine conversion. Preserve the approved plan and earlier scene state rather than destructively replacing them.

## Model and review in passes

1. **Spatial blockout:** establish overall footprint, levels, walls, openings, circulation, and major furniture. Review a plan/top or untextured solid view before adding detail.
2. **Geometry check:** inspect wall joins, door/window openings, object intersections, scale, normals, and representative paths through the space. Use scripted checks where practical, then inspect the scene visually. A few checks do not certify every possible clash or code requirement.
3. **Camera-led detail:** add joinery, furniture, fixtures, and everyday objects at the level of detail visible from planned camera distances. Model functional openings or hollow forms when close views depend on them; use simpler geometry for distant objects.
4. **Materials and light:** set real-world texture scale and orientation; tune roughness, reflectance, and surface variation to the source material. Make visible fixtures the plausible source of local light, and remove fill lighting that flattens the space. Treat asset provenance and licenses explicitly.
5. **Preview loop:** render low-cost previews from the intended views, inspect composition, geometry readability, intersections, clipping, exposure, and material response, make targeted changes, and preview again. Commit to final-resolution stills or animation only after the framing and design direction are accepted.

Review two complementary outputs: a rendered view for atmosphere, materials, and composition; and an untextured/solid view for layout, openings, and geometry. A good render alone is not evidence that the model is spatially correct.

## Tours, real-time handoff, and comparison boards

- For a camera tour, define audience, route, duration, viewpoint height, lens/FOV, pacing, transitions, and focal moments before producing final frames. Render and review previews first; check that the camera shows the intended rooms and connections, avoids blank-wall pauses and awkward endings, and does not pass through geometry.
- For an optional Unreal or other real-time handoff, export evaluated geometry and a scene manifest that records object identity, transforms, units, coordinate convention, material/texture assignments, lights, cameras, instances, and collision intent. Convert units and axes deliberately; inspect material translation and rebuild only what the target engine cannot represent directly. Reopen and walk the converted scene to verify it.
- When comparing design options or render engines, use the same subjects, camera positions, orientation, field of view, crop, and label hierarchy. Identify differences in lighting/material systems rather than implying pixel-identical output.
- Storyboards should preserve whole views unless cropping is intentional; provide legible labels, consistent sequence, and captions that explain the comparison.

## Delivery boundary

State whether each output is a concept visualization, a dimensionally informed design model, or a coordinated technical model. Include the native editable project when requested, plus exported stills/video and any transfer manifest needed for downstream use. Disclose approximations, missing source information, and failed validation. Concept visualization does not establish structural adequacy, code compliance, accessibility, or construction readiness; those require project-specific professional review.
