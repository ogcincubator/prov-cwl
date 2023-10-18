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
