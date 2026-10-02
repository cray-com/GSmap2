# Proposed upstream PR

Status: prepared, not submitted. This is a documentation-only change for
[hzguz/GSmap](https://github.com/hzguz/GSmap), not a PR of the entire GSmap2 fork.

Branch: [cray-com/GSmap:docs/svg-export-limitations](https://github.com/cray-com/GSmap/tree/docs/svg-export-limitations)

[Open the upstream comparison](https://github.com/hzguz/GSmap/compare/main...cray-com:docs/svg-export-limitations)

## Suggested title

Clarify which layers and paint effects the local SVG export supports

## Suggested body

Thanks for creating GSmap, Gustavo. It has been a useful starting point for
building quick map visualizations for design layouts.

The README currently describes an SVG that mirrors the preview, while its
limitations section explains that symbols and some paint effects are omitted
or approximated. This small PR brings those limitations into the introduction
and export instructions so users can choose the right format before exporting.

### Changes

- Describe SVG as editable supported geometry rather than a complete copy of the preview.
- Mention omitted place/street labels and POI icons near the export instructions.
- Mention pattern fallbacks and per-layer paint approximations.
- Recommend PNG when the rendered appearance, text and icons matter.

### Evidence and checks

The current `VECTORIZABLE_LAYER_TYPES` includes `fill`, `fill-extrusion`, `line`
and `background`, but not `symbol`. Paint is resolved once per layer using the
first feature's properties. The existing README already documents these
limitations. No runtime code or dependencies change, and `git diff --check`
passes. This PR does not implement SVG text reconstruction or claim a new
browser reproduction.

## Later contributions

JSON/GeoJSON import and native point/label styling could be offered in a separate
PR if Gustavo wants that feature. Keep GSmap2 branding, the Vienna default,
printing UI and palette additions out of that contribution. The larger PNG
renderer should receive a complete browser export check before being offered
as a tested upstream fix.
