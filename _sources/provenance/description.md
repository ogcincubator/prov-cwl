## Provenance profile

This is a profile of the JSON schema for PROV-O.

> This demonstrates inheritance of the JSON-LD binding from the schema to the PROV-O ontology.

The template provides for a sample profile that extends the underlying provenance model through:
- defining specific Entity and Activity types
- adds example metadata attributes for provenance classes
- defines a SHACL rule for checking presence of specific types

## components

under a building block directory _/example-prov-profile:
- schema.yaml extends the [base](https://ogcincubator.github.io/bblock-prov-schema) and shows how to define additional schema elements
- context.jsonld defines URI bindings for customisations and bases for keywords (e.g. activity and entity types)
- rules.shacl defines logical consistency rules for the profile (what types of activities etc.)

Note that compliance with general PROV patterns is handled by inheritance of SHACL rules from the base profile.

## Relation to the generic W3C PROV profiles

This block's schema is built on [`ogc.ogc-utils.prov`](bblocks://ogc.ogc-utils.prov) (the OGC PROV
Chain / "Single Schema for PROV"), and follows the same nested-object-plus-JSON-LD-context pattern
as [`W3C PROV-JSONLD`](bblocks://ogc.ogc-utils.prov.w3c-prov-jsonld) - this profile is declared
(`isProfileOf`) as a further specialization of both. Its own `context.jsonld` adds the CWL-specific
vocabulary (`wfdesc`, `wfprov`, `cwlprov`, etc.) needed to describe workflow runs.

The [`turtle`](bblocks://ogc.profiles.prov.cwl.turtle) sibling block in this register represents the
same CWL provenance content as RDF/Turtle rather than JSON-LD - the two are cross-linked via
`hasFormat`, the same relation used among the generic W3C PROV representations.

## Relation to CWL workflow definitions

A provenance record's `qualifiedAssociation.hadPlan` entities (see the examples) identify the CWL
workflow or tool that was actually run - a `prov:Plan` in PROV terms. This block declares a
`dependsOn` [`ogc.cwl.v1_2_1.CWL`](bblocks://ogc.cwl.v1_2_1.CWL): the provenance record is an
execution trace whose `Plan` entities are instances of a CWL document defined by that block, rather
than a schema-level specialization of it.
