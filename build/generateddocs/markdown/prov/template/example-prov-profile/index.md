
# Provenance Profile (Schema)

`ogc.prov.template.example-prov-profile` *v0.1*

This is a template for creating a customised profile of the PROV schema building block.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

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

## Examples

### Profile example
JSON
#### json
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

#### jsonld
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

#### ttl
```ttl


```

## Schema

```yaml
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

Links to the schema:

* YAML version: [schema.yaml](https://raw.githubusercontent.com/ogcincubator/prov-profile-template/master/build/annotated/prov/template/example-prov-profile/schema.json)
* JSON version: [schema.json](https://raw.githubusercontent.com/ogcincubator/prov-profile-template/master/build/annotated/prov/template/example-prov-profile/schema.yaml)


# JSON-LD Context

```jsonld
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

You can find the full JSON-LD context here:
[context.jsonld](https://raw.githubusercontent.com/ogcincubator/prov-profile-template/master/build/annotated/prov/template/example-prov-profile/context.jsonld)


# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/ogcincubator/prov-profile-template](https://github.com/ogcincubator/prov-profile-template)
* Path: `_sources/example-prov-profile`

