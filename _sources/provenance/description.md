## Provenance profile

This is a profile of the JSON schema for PROV-O, using the CWLPROV vocabulary to describe the
execution of Common Workflow Language (CWL) workflows and tools.

> This demonstrates inheritance of the JSON-LD binding from the schema to the PROV-O ontology.

This block reuses the underlying provenance model as-is (no additional schema constraints), and adds
a JSON-LD `context.jsonld` binding the CWL/CWLPROV-specific vocabulary (workflow, process, and
association types) used by real `cwltool` provenance output.

## components

This block's [source directory](https://github.com/ogcincubator/prov-cwl/tree/master/_sources/provenance)
contains:
- [`schema.yaml`](https://github.com/ogcincubator/prov-cwl/blob/master/_sources/provenance/schema.yaml),
  which references the [base OGC PROV Chain schema](https://ogcincubator.github.io/bblock-prov-schema)
  without further constraining it
- [`context.jsonld`](https://github.com/ogcincubator/prov-cwl/blob/master/_sources/provenance/context.jsonld),
  which adds the CWL/CWLPROV-specific URI bindings (`wf`, `wfdesc`, `wfprov`, `cwlprov`, `schemaorg`,
  `foaf`) referenced by the examples

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
