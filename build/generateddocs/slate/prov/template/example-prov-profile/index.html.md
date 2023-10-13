---
title: Provenance Profile (Schema)

language_tabs:
  - json: JSON
  - jsonld: JSON-LD

toc_footers:
  - Version 0.1
  - <a href='#'>Provenance Profile</a>
  - <a href='https://blocks.ogc.org/register.html'>Building Blocks register</a>

search: true

code_clipboard: true

meta:
  - name: Provenance Profile (Schema)
---


# Provenance Profile `ogc.prov.template.example-prov-profile`

This is a template for creating a customised profile of the PROV schema building block.

<p class="status">
    <span data-rainbow-uri="http://www.opengis.net/def/status">Status</span>:
    <a href="http://www.opengis.net/def/status/under-development" target="_blank" data-rainbow-uri>Under development</a>
</p>

<aside class="success">
This building block is <strong><a href="https://github.com/ogcincubator/prov-profile-template/blob/master/build/tests/prov/template/example-prov-profile/" target="_blank">valid</a></strong>
</aside>

# Description

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

# Examples

## Profile example

JSON



```json
{
  "id": "ProvProfile",
  "name": "EntityExample",
  "featureType": "MyEntityType",
  "wasGeneratedBy": {
    "type": "Activity",
    "activity": "MyActivity",
    "extraProperty": "",
    "endedAtTime": "2029-01-01"
  }
}
```

<blockquote class="lang-specific json">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/ogcincubator/prov-profile-template/master/build/tests/prov/template/example-prov-profile/example_1_1.json">Open in new window</a>
    <a target="_blank" href="https://avillar.github.io/TreedocViewer/?dataParser=json&amp;dataUrl=https%3A%2F%2Fraw.githubusercontent.com%2Fogcincubator%2Fprov-profile-template%2Fmaster%2Fbuild%2Ftests%2Fprov%2Ftemplate%2Fexample-prov-profile%2Fexample_1_1.json&amp;expand=2&amp;option=%7B%22showTable%22%3A+false%7D">View on JSON Viewer</a></p>
</blockquote>




```jsonld
{
  "id": "ProvProfile",
  "name": "EntityExample",
  "featureType": "MyEntityType",
  "wasGeneratedBy": {
    "type": "Activity",
    "activity": "MyActivity",
    "extraProperty": "",
    "endedAtTime": "2029-01-01"
  },
  "@context": "https://raw.githubusercontent.com/ogcincubator/prov-profile-template/master/build/annotated/prov/template/example-prov-profile/context.jsonld"
}
```

<blockquote class="lang-specific jsonld">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/ogcincubator/prov-profile-template/master/build/tests/prov/template/example-prov-profile/example_1_1.jsonld">Open in new window</a>
    <a target="_blank" href="https://json-ld.org/playground/#json-ld=https%3A%2F%2Fraw.githubusercontent.com%2Fogcincubator%2Fprov-profile-template%2Fmaster%2Fbuild%2Ftests%2Fprov%2Ftemplate%2Fexample-prov-profile%2Fexample_1_1.jsonld">View on JSON-LD Playground</a>
</blockquote>




# JSON Schema

```yaml--schema
description: Example profile schema
$defs:
  MyActivity:
    $anchor: MyActivity
    allOf:
    - ref: https://ogcincubator.github.io/bblock-prov-schema/build/annotated/ogc-utils/prov/schema.yaml#/$defs/Activity
    - type: object
      properties:
        extraProperty:
          type: string
          description: Just an extra property that MyActivity has
      required:
      - extraProperty
type: object
allOf:
- ref: https://ogcincubator.github.io/bblock-prov-schema/build/annotated/ogc-utils/prov/schema.yaml
x-jsonld-extra-terms:
  extraProperty: http://mymodel.eg/ont/extraProperty
  featureType:
    x-jsonld-context:
      '@base': http://mymodel.eg/EntityTypes/
  activity:
    x-jsonld-context:
      '@base': http://mymodel.eg/activityTypes/

```

> <a target="_blank" href="https://avillar.github.io/TreedocViewer/?dataParser=yaml&amp;dataUrl=https%3A%2F%2Fraw.githubusercontent.com%2Fogcincubator%2Fprov-profile-template%2Fmaster%2Fbuild%2Fannotated%2Fprov%2Ftemplate%2Fexample-prov-profile%2Fschema.yaml&amp;expand=2&amp;option=%7B%22showTable%22%3A+false%7D">View on YAML Viewer</a>

Links to the schema:

* YAML version: <a href="https://raw.githubusercontent.com/ogcincubator/prov-profile-template/master/build/annotated/prov/template/example-prov-profile/schema.yaml" target="_blank">https://raw.githubusercontent.com/ogcincubator/prov-profile-template/master/build/annotated/prov/template/example-prov-profile/schema.yaml</a>
* JSON version: <a href="https://raw.githubusercontent.com/ogcincubator/prov-profile-template/master/build/annotated/prov/template/example-prov-profile/schema.json" target="_blank">https://raw.githubusercontent.com/ogcincubator/prov-profile-template/master/build/annotated/prov/template/example-prov-profile/schema.json</a>


# JSON-LD Context

```json--ldContext
{
  "@context": {
    "extraProperty": "http://mymodel.eg/ont/extraProperty",
    "@base": "http://mymodel.eg/activityTypes/",
    "featureType": {
      "x-jsonld-context": {
        "@base": "http://mymodel.eg/EntityTypes/"
      }
    },
    "activity": {
      "x-jsonld-context": {
        "@base": "http://mymodel.eg/activityTypes/"
      }
    },
    "@version": 1.1
  }
}
```

> <a target="_blank" href="https://json-ld.org/playground/#json-ld=https%3A%2F%2Fraw.githubusercontent.com%2Fogcincubator%2Fprov-profile-template%2Fmaster%2Fbuild%2Fannotated%2Fprov%2Ftemplate%2Fexample-prov-profile%2Fcontext.jsonld">View on JSON-LD Playground</a>

You can find the full JSON-LD context here:
<a href="https://raw.githubusercontent.com/ogcincubator/prov-profile-template/master/build/annotated/prov/template/example-prov-profile/context.jsonld" target="_blank">https://raw.githubusercontent.com/ogcincubator/prov-profile-template/master/build/annotated/prov/template/example-prov-profile/context.jsonld</a>

# For developers

The source code for this Building Block can be found in the following repository:

* URL: <a href="https://github.com/ogcincubator/prov-profile-template" target="_blank">https://github.com/ogcincubator/prov-profile-template</a>
* Path:
<code><a href="https://github.com/ogcincubator/prov-profile-template/blob/HEAD/_sources/example-prov-profile" target="_blank">_sources/example-prov-profile</a></code>

