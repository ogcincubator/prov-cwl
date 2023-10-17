---
title: Provenance Profile (Schema)

language_tabs:
  - json: JSON
  - jsonld: JSON-LD
  - turtle: RDF/Turtle

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
    <a href="http://www.opengis.net/def/status/invalid" target="_blank" data-rainbow-uri>Invalid</a>
</p>

<aside class="warning">
Validation for this building block has <strong><a href="https://github.com/ogcincubator/prov-cwl/blob/master/build/tests/prov/template/example-prov-profile/" target="_blank">failed</a></strong>
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
    "endedAtTime": "2029-01-01T22:05:01Z"
  }
}
```

<blockquote class="lang-specific json">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/ogcincubator/prov-cwl/master/build/tests/prov/template/example-prov-profile/example_1_1.json">Open in new window</a>
    <a target="_blank" href="https://avillar.github.io/TreedocViewer/?dataParser=json&amp;dataUrl=https%3A%2F%2Fraw.githubusercontent.com%2Fogcincubator%2Fprov-cwl%2Fmaster%2Fbuild%2Ftests%2Fprov%2Ftemplate%2Fexample-prov-profile%2Fexample_1_1.json&amp;expand=2&amp;option=%7B%22showTable%22%3A+false%7D">View on JSON Viewer</a></p>
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
    "endedAtTime": "2029-01-01T22:05:01Z"
  },
  "@context": "https://raw.githubusercontent.com/ogcincubator/prov-cwl/master/build/annotated/prov/template/example-prov-profile/context.jsonld"
}
```

<blockquote class="lang-specific jsonld">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/ogcincubator/prov-cwl/master/build/tests/prov/template/example-prov-profile/example_1_1.jsonld">Open in new window</a>
    <a target="_blank" href="https://json-ld.org/playground/#json-ld=https%3A%2F%2Fraw.githubusercontent.com%2Fogcincubator%2Fprov-cwl%2Fmaster%2Fbuild%2Ftests%2Fprov%2Ftemplate%2Fexample-prov-profile%2Fexample_1_1.jsonld">View on JSON-LD Playground</a>
</blockquote>




```turtle
@prefix dct: <http://purl.org/dc/terms/> .
@prefix prov: <http://www.w3.org/ns/prov#> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

<file:///github/workspace/ProvProfile> rdfs:label "EntityExample" ;
    prov:wasGeneratedBy [ dct:type "Activity" ;
            prov:endedAtTime "2029-01-01T22:05:01+00:00"^^xsd:dateTime ] .


```

<blockquote class="lang-specific turtle">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/ogcincubator/prov-cwl/master/build/tests/prov/template/example-prov-profile/example_1_1.ttl">Open in new window</a>
</blockquote>



## Profile example

JSON



```json
{
  "id": "uuid:071d1b5c-1b2b-4995-a6e0-80821af85abd",
  "type": [
    "Entity",
    "wf4ever:File",
    "wfprov:Artifact"
  ],
  "qualifiedGeneration": [
    {
      "type": "Generation",
      "activity": {
        "id": "uuid:d7e8b17e-2d80-4c42-a797-bc3628f52c44",
        "type": [
          "wfprov:ProcessRun",
          "Activity"
        ],
        "name": "Run of workflow/packed.cwl#main/sorted",
        "qualifiedAssociation": {
          "type": "Association",
          "hadPlan": {
            "id":" wf:main/sorted",
            "type": [
              "Entity",
              "Plan",
              "wfdesc:Process"
            ]
          }
        },
        "qualifiedEnd": {
          "type": "End",
          "atTime": "2018-10-25T15:46:38.069110",
          "hadActivity": {
            "id": "uuid:1f767ad4-ac52-4623-b5bc-dd9faf2b869f",
            "type": [
              "wfprov:WorkflowRun",
              "Activity"
            ],
            "name": "Run of workflow/packed.cwl#main",
            "qualifiedAssociation": {
              "type": "Association",
              "hadPlan": {
                "id": "wf:main",
                "type": [
                  "Entity",
                  "Plan",
                  "wfdesc:Workflow"
                ],
                "wfdesc:hasSubProcess": [
                  {
                    "id": "wf:main/rev",
                    "type": [
                      "Plan",
                      "Entity",
                      "wfdesc:Process"
                    ]
                  },
                  {
                    "id": "wf:main/sorted"
                  }
                ],
                "name": "Prospective provenance"
              }
            },
            "qualifiedEnd": {
              "type": "End",
              "atTime": "2018-10-25T15:46:43.020168",
              "hadActivity": {
                "id": "uuid:ac9c1653-4291-47bc-86f8-6dedcff13519",
                "type": [
                  "Agent",
                  "SoftwareAgent",
                  "wfprov:WorkflowEngine"
                ],
                "name": "cwltool 1.0.20181012180214",
                "qualifiedStart": {
                  "type": "Start",
                  "atTime": "2018-10-25T15:46:35.210973",
                  "hadActivity": {
                    "id": "uuid:7fa2c8d0-9a3e-4512-9171-fc3b729c2210",
                    "type": "Agent",
                    "actedOnBehalfOf": {
                      "id": "https://orcid.org/0000-0001-9842-9718",
                      "type": [
                        "schemaorg:Person",
                        "Person",
                        "Agent"
                      ],
                      "schemaorg:name": "Stian Soiland-Reyes",
                      "name": "Stian Soiland-Reyes",
                      "foaf:name": "Stian Soiland-Reyes"
                    }
                  }
                }
              }
            },
            "qualifiedStart": {
              "type": "Start",
              "atTime": "2018-10-25T15:46:35.211153",
              "hadActivity": "uuid:ac9c1653-4291-47bc-86f8-6dedcff13519"
            },
            "qualifiedUsage": [
              {
                "type": "Usage",
                "atTime": "2018-10-25T15:46:35.303484",
                "entity": {
                  "id": "uuid:fe16801a-7995-4968-a8bb-5e9d46255bb7",
                  "type": [
                    "Entity",
                    "wfprov:Artifact",
                    "wf4ever:File"
                  ],
                  "specializationOf": {
                    "id": "sha1:327fc7aedf4f6b69a42a7c8b808dc5a7aff61376",
                    "type": [
                      "wfprov:Artifact",
                      "Entity"
                    ]
                  },
                  "cwlprov:basename": "whale.txt",
                  "cwlprov:nameext": ".txt",
                  "cwlprov:nameroot": "whale"
                },
                "hadRole": "wf:main/input"
              },
              {
                "type": "Usage",
                "atTime": "2018-10-25T15:46:35.303643",
                "entity": {
                  "id": "uuid:ed8d007b-a1f3-4bfe-b390-08df074d712d",
                  "type": "Entity",
                  "value": true
                },
                "hadRole": "wf:main/reverse_sort"
              }
            ],
            "startedAtTime": "2018-10-25T15:46:35.211026",
            "wasAssociatedWith": "uuid:ac9c1653-4291-47bc-86f8-6dedcff13519"
          }
        },
        "qualifiedStart": {
          "type": "Start",
          "atTime": "2018-10-25T15:46:36.975235",
          "hadActivity": "uuid:1f767ad4-ac52-4623-b5bc-dd9faf2b869f"
        },
        "qualifiedUsage": [
          {
            "type": "Usage",
            "atTime": "2018-10-25T15:46:37.067604",
            "entity": {
              "id": "uuid:feabfc2c-e5eb-49d0-ad5c-c19076482265",
              "type": [
                "wf4ever:File",
                "wfprov:Artifact",
                "Entity"
              ],
              "qualifiedGeneration": {
                "type": "Generation",
                "activity": {
                  "id": "uuid:f81dd60b-46db-4e58-b9f9-5606de1f10de",
                  "type": [
                    "wfprov:ProcessRun",
                    "Activity"
                  ],
                  "name": "Run of workflow/packed.cwl#main/rev",
                  "qualifiedAssociation": {
                    "type": "Association",
                    "hadPlan": "wf:main/rev"
                  },
                  "qualifiedEnd": {
                    "type": "End",
                    "atTime": "2018-10-25T15:46:36.967359",
                    "hadActivity": "uuid:1f767ad4-ac52-4623-b5bc-dd9faf2b869f"
                  },
                  "qualifiedStart": {
                    "type": "Start",
                    "atTime": "2018-10-25T15:46:35.314101",
                    "hadActivity": "uuid:1f767ad4-ac52-4623-b5bc-dd9faf2b869f"
                  },
                  "qualifiedUsage": {
                    "type": "Usage",
                    "atTime": "2018-10-25T15:46:35.597726",
                    "entity": {
                      "id": "uuid:6e84364f-faa9-4a27-aaba-5e4b80d9564b",
                      "type": [
                        "wfprov:Artifact",
                        "wf4ever:File",
                        "Entity"
                      ],
                      "specializationOf": "sha1:327fc7aedf4f6b69a42a7c8b808dc5a7aff61376",
                      "cwlprov:basename": "whale.txt",
                      "cwlprov:nameext": ".txt",
                      "cwlprov:nameroot": "whale"
                    },
                    "hadRole": "wf:main/rev/input"
                  },
                  "wasAssociatedWith": [
                    {
                      "id": "uuid:f5ce6344-3b3b-4653-84fd-1f5abfa57fb0",
                      "type": [
                        "SoftwareAgent",
                        "Agent"
                      ],
                      "name": "Container execution of image debian:8",
                      "cwlprov:image": "debian:8"
                    },
                    "uuid:ac9c1653-4291-47bc-86f8-6dedcff13519"
                  ]
                },
                "atTime": "2018-10-25T15:46:36.963254",
                "hadRole": "wf:main/rev/output"
              },
              "specializationOf": {
                "id": "sha1:97fe1b50b4582cebc7d853796ebd62e3e163aa3f",
                "type": [
                  "Entity",
                  "wfprov:Artifact"
                ]
              },
              "cwlprov:basename": "output.txt",
              "cwlprov:nameext": ".txt",
              "cwlprov:nameroot": "output"
            },
            "hadRole": "wf:main/sorted/input"
          },
          {
            "type": "Usage",
            "atTime": "2018-10-25T15:46:37.067864",
            "entity": {
              "id": "uuid:4ab5a3fe-e481-4f7f-98c4-af8e5dfccb93",
              "type": "Entity",
              "value": true
            },
            "hadRole": "wf:main/sorted/reverse"
          }
        ],
        "wasAssociatedWith": [
          "uuid:ac9c1653-4291-47bc-86f8-6dedcff13519",
          {
            "id": "uuid:ba0fe122-124e-417b-8a2a-95e721320a2d",
            "type": [
              "SoftwareAgent",
              "Agent"
            ],
            "name": "Container execution of image debian:8",
            "cwlprov:image": "debian:8"
          }
        ]
      },
      "atTime": "2018-10-25T15:46:38.058365",
      "hadRole": "wf:main/sorted/output"
    },
    {
      "type": "Generation",
      "activity": "uuid:1f767ad4-ac52-4623-b5bc-dd9faf2b869f",
      "atTime": "2018-10-25T15:46:43.020002",
      "hadRole": "wf:main/primary/output"
    }
  ],
  "specializationOf": {
    "id": "sha1:b9214658cc453331b62c2282b772a5c063dbd284",
    "type": [
      "Entity",
      "wfprov:Artifact"
    ]
  },
  "cwlprov:basename": "output.txt",
  "cwlprov:nameext": ".txt",
  "cwlprov:nameroot": "output"
}
```

<blockquote class="lang-specific json">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/ogcincubator/prov-cwl/master/build/tests/prov/template/example-prov-profile/example_2_1.json">Open in new window</a>
    <a target="_blank" href="https://avillar.github.io/TreedocViewer/?dataParser=json&amp;dataUrl=https%3A%2F%2Fraw.githubusercontent.com%2Fogcincubator%2Fprov-cwl%2Fmaster%2Fbuild%2Ftests%2Fprov%2Ftemplate%2Fexample-prov-profile%2Fexample_2_1.json&amp;expand=2&amp;option=%7B%22showTable%22%3A+false%7D">View on JSON Viewer</a></p>
</blockquote>




```jsonld
{
  "id": "uuid:071d1b5c-1b2b-4995-a6e0-80821af85abd",
  "type": [
    "Entity",
    "wf4ever:File",
    "wfprov:Artifact"
  ],
  "qualifiedGeneration": [
    {
      "type": "Generation",
      "activity": {
        "id": "uuid:d7e8b17e-2d80-4c42-a797-bc3628f52c44",
        "type": [
          "wfprov:ProcessRun",
          "Activity"
        ],
        "name": "Run of workflow/packed.cwl#main/sorted",
        "qualifiedAssociation": {
          "type": "Association",
          "hadPlan": {
            "id": " wf:main/sorted",
            "type": [
              "Entity",
              "Plan",
              "wfdesc:Process"
            ]
          }
        },
        "qualifiedEnd": {
          "type": "End",
          "atTime": "2018-10-25T15:46:38.069110",
          "hadActivity": {
            "id": "uuid:1f767ad4-ac52-4623-b5bc-dd9faf2b869f",
            "type": [
              "wfprov:WorkflowRun",
              "Activity"
            ],
            "name": "Run of workflow/packed.cwl#main",
            "qualifiedAssociation": {
              "type": "Association",
              "hadPlan": {
                "id": "wf:main",
                "type": [
                  "Entity",
                  "Plan",
                  "wfdesc:Workflow"
                ],
                "wfdesc:hasSubProcess": [
                  {
                    "id": "wf:main/rev",
                    "type": [
                      "Plan",
                      "Entity",
                      "wfdesc:Process"
                    ]
                  },
                  {
                    "id": "wf:main/sorted"
                  }
                ],
                "name": "Prospective provenance"
              }
            },
            "qualifiedEnd": {
              "type": "End",
              "atTime": "2018-10-25T15:46:43.020168",
              "hadActivity": {
                "id": "uuid:ac9c1653-4291-47bc-86f8-6dedcff13519",
                "type": [
                  "Agent",
                  "SoftwareAgent",
                  "wfprov:WorkflowEngine"
                ],
                "name": "cwltool 1.0.20181012180214",
                "qualifiedStart": {
                  "type": "Start",
                  "atTime": "2018-10-25T15:46:35.210973",
                  "hadActivity": {
                    "id": "uuid:7fa2c8d0-9a3e-4512-9171-fc3b729c2210",
                    "type": "Agent",
                    "actedOnBehalfOf": {
                      "id": "https://orcid.org/0000-0001-9842-9718",
                      "type": [
                        "schemaorg:Person",
                        "Person",
                        "Agent"
                      ],
                      "schemaorg:name": "Stian Soiland-Reyes",
                      "name": "Stian Soiland-Reyes",
                      "foaf:name": "Stian Soiland-Reyes"
                    }
                  }
                }
              }
            },
            "qualifiedStart": {
              "type": "Start",
              "atTime": "2018-10-25T15:46:35.211153",
              "hadActivity": "uuid:ac9c1653-4291-47bc-86f8-6dedcff13519"
            },
            "qualifiedUsage": [
              {
                "type": "Usage",
                "atTime": "2018-10-25T15:46:35.303484",
                "entity": {
                  "id": "uuid:fe16801a-7995-4968-a8bb-5e9d46255bb7",
                  "type": [
                    "Entity",
                    "wfprov:Artifact",
                    "wf4ever:File"
                  ],
                  "specializationOf": {
                    "id": "sha1:327fc7aedf4f6b69a42a7c8b808dc5a7aff61376",
                    "type": [
                      "wfprov:Artifact",
                      "Entity"
                    ]
                  },
                  "cwlprov:basename": "whale.txt",
                  "cwlprov:nameext": ".txt",
                  "cwlprov:nameroot": "whale"
                },
                "hadRole": "wf:main/input"
              },
              {
                "type": "Usage",
                "atTime": "2018-10-25T15:46:35.303643",
                "entity": {
                  "id": "uuid:ed8d007b-a1f3-4bfe-b390-08df074d712d",
                  "type": "Entity",
                  "value": true
                },
                "hadRole": "wf:main/reverse_sort"
              }
            ],
            "startedAtTime": "2018-10-25T15:46:35.211026",
            "wasAssociatedWith": "uuid:ac9c1653-4291-47bc-86f8-6dedcff13519"
          }
        },
        "qualifiedStart": {
          "type": "Start",
          "atTime": "2018-10-25T15:46:36.975235",
          "hadActivity": "uuid:1f767ad4-ac52-4623-b5bc-dd9faf2b869f"
        },
        "qualifiedUsage": [
          {
            "type": "Usage",
            "atTime": "2018-10-25T15:46:37.067604",
            "entity": {
              "id": "uuid:feabfc2c-e5eb-49d0-ad5c-c19076482265",
              "type": [
                "wf4ever:File",
                "wfprov:Artifact",
                "Entity"
              ],
              "qualifiedGeneration": {
                "type": "Generation",
                "activity": {
                  "id": "uuid:f81dd60b-46db-4e58-b9f9-5606de1f10de",
                  "type": [
                    "wfprov:ProcessRun",
                    "Activity"
                  ],
                  "name": "Run of workflow/packed.cwl#main/rev",
                  "qualifiedAssociation": {
                    "type": "Association",
                    "hadPlan": "wf:main/rev"
                  },
                  "qualifiedEnd": {
                    "type": "End",
                    "atTime": "2018-10-25T15:46:36.967359",
                    "hadActivity": "uuid:1f767ad4-ac52-4623-b5bc-dd9faf2b869f"
                  },
                  "qualifiedStart": {
                    "type": "Start",
                    "atTime": "2018-10-25T15:46:35.314101",
                    "hadActivity": "uuid:1f767ad4-ac52-4623-b5bc-dd9faf2b869f"
                  },
                  "qualifiedUsage": {
                    "type": "Usage",
                    "atTime": "2018-10-25T15:46:35.597726",
                    "entity": {
                      "id": "uuid:6e84364f-faa9-4a27-aaba-5e4b80d9564b",
                      "type": [
                        "wfprov:Artifact",
                        "wf4ever:File",
                        "Entity"
                      ],
                      "specializationOf": "sha1:327fc7aedf4f6b69a42a7c8b808dc5a7aff61376",
                      "cwlprov:basename": "whale.txt",
                      "cwlprov:nameext": ".txt",
                      "cwlprov:nameroot": "whale"
                    },
                    "hadRole": "wf:main/rev/input"
                  },
                  "wasAssociatedWith": [
                    {
                      "id": "uuid:f5ce6344-3b3b-4653-84fd-1f5abfa57fb0",
                      "type": [
                        "SoftwareAgent",
                        "Agent"
                      ],
                      "name": "Container execution of image debian:8",
                      "cwlprov:image": "debian:8"
                    },
                    "uuid:ac9c1653-4291-47bc-86f8-6dedcff13519"
                  ]
                },
                "atTime": "2018-10-25T15:46:36.963254",
                "hadRole": "wf:main/rev/output"
              },
              "specializationOf": {
                "id": "sha1:97fe1b50b4582cebc7d853796ebd62e3e163aa3f",
                "type": [
                  "Entity",
                  "wfprov:Artifact"
                ]
              },
              "cwlprov:basename": "output.txt",
              "cwlprov:nameext": ".txt",
              "cwlprov:nameroot": "output"
            },
            "hadRole": "wf:main/sorted/input"
          },
          {
            "type": "Usage",
            "atTime": "2018-10-25T15:46:37.067864",
            "entity": {
              "id": "uuid:4ab5a3fe-e481-4f7f-98c4-af8e5dfccb93",
              "type": "Entity",
              "value": true
            },
            "hadRole": "wf:main/sorted/reverse"
          }
        ],
        "wasAssociatedWith": [
          "uuid:ac9c1653-4291-47bc-86f8-6dedcff13519",
          {
            "id": "uuid:ba0fe122-124e-417b-8a2a-95e721320a2d",
            "type": [
              "SoftwareAgent",
              "Agent"
            ],
            "name": "Container execution of image debian:8",
            "cwlprov:image": "debian:8"
          }
        ]
      },
      "atTime": "2018-10-25T15:46:38.058365",
      "hadRole": "wf:main/sorted/output"
    },
    {
      "type": "Generation",
      "activity": "uuid:1f767ad4-ac52-4623-b5bc-dd9faf2b869f",
      "atTime": "2018-10-25T15:46:43.020002",
      "hadRole": "wf:main/primary/output"
    }
  ],
  "specializationOf": {
    "id": "sha1:b9214658cc453331b62c2282b772a5c063dbd284",
    "type": [
      "Entity",
      "wfprov:Artifact"
    ]
  },
  "cwlprov:basename": "output.txt",
  "cwlprov:nameext": ".txt",
  "cwlprov:nameroot": "output",
  "@context": "https://raw.githubusercontent.com/ogcincubator/prov-cwl/master/build/annotated/prov/template/example-prov-profile/context.jsonld"
}
```

<blockquote class="lang-specific jsonld">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/ogcincubator/prov-cwl/master/build/tests/prov/template/example-prov-profile/example_2_1.jsonld">Open in new window</a>
    <a target="_blank" href="https://json-ld.org/playground/#json-ld=https%3A%2F%2Fraw.githubusercontent.com%2Fogcincubator%2Fprov-cwl%2Fmaster%2Fbuild%2Ftests%2Fprov%2Ftemplate%2Fexample-prov-profile%2Fexample_2_1.jsonld">View on JSON-LD Playground</a>
</blockquote>




```turtle
@prefix cwlprov: <https://w3id.org/cwl/prov#> .
@prefix dct: <http://purl.org/dc/terms/> .
@prefix foaf: <http://xmlns.com/foaf/0.1/> .
@prefix prov: <http://www.w3.org/ns/prov#> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix schemaorg: <http://schema.org/> .
@prefix sha1: <urn:hash::sha1:> .
@prefix uuid: <urn:uuid:> .
@prefix wf: <arcp://uuid,1f767ad4-ac52-4623-b5bc-dd9faf2b869f/workflow/packed.cwl#> .
@prefix wfdesc: <http://purl.org/wf4ever/wfdesc#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

uuid:071d1b5c-1b2b-4995-a6e0-80821af85abd dct:type "Entity",
        "wf4ever:File",
        "wfprov:Artifact" ;
    prov:qualifiedGeneration [ dct:type "Generation" ;
            prov:activity uuid:1f767ad4-ac52-4623-b5bc-dd9faf2b869f ;
            prov:atTime "2018-10-25T15:46:43.020002"^^xsd:dateTime ],
        [ dct:type "Generation" ;
            prov:activity uuid:d7e8b17e-2d80-4c42-a797-bc3628f52c44 ;
            prov:atTime "2018-10-25T15:46:38.058365"^^xsd:dateTime ] ;
    prov:specializationOf sha1:b9214658cc453331b62c2282b772a5c063dbd284 ;
    cwlprov:basename "output.txt" ;
    cwlprov:nameext ".txt" ;
    cwlprov:nameroot "output" .

wf:main rdfs:label "Prospective provenance" ;
    dct:type "Entity",
        "Plan",
        "wfdesc:Workflow" ;
    wfdesc:hasSubProcess <arcp://uuid,1f767ad4-ac52-4623-b5bc-dd9faf2b869f/workflow/packed.cwl#main/rev>,
        <arcp://uuid,1f767ad4-ac52-4623-b5bc-dd9faf2b869f/workflow/packed.cwl#main/sorted> .

<https://orcid.org/0000-0001-9842-9718> rdfs:label "Stian Soiland-Reyes" ;
    dct:type "Agent",
        "Person",
        "schemaorg:Person" ;
    schemaorg:name "Stian Soiland-Reyes" ;
    foaf:name "Stian Soiland-Reyes" .

sha1:97fe1b50b4582cebc7d853796ebd62e3e163aa3f dct:type "Entity",
        "wfprov:Artifact" .

sha1:b9214658cc453331b62c2282b772a5c063dbd284 dct:type "Entity",
        "wfprov:Artifact" .

uuid:4ab5a3fe-e481-4f7f-98c4-af8e5dfccb93 dct:type "Entity" ;
    prov:value true .

uuid:6e84364f-faa9-4a27-aaba-5e4b80d9564b dct:type "Entity",
        "wf4ever:File",
        "wfprov:Artifact" ;
    prov:specializationOf sha1:327fc7aedf4f6b69a42a7c8b808dc5a7aff61376 ;
    cwlprov:basename "whale.txt" ;
    cwlprov:nameext ".txt" ;
    cwlprov:nameroot "whale" .

uuid:7fa2c8d0-9a3e-4512-9171-fc3b729c2210 dct:type "Agent" ;
    prov:actedOnBehalfOf <https://orcid.org/0000-0001-9842-9718> .

uuid:ba0fe122-124e-417b-8a2a-95e721320a2d rdfs:label "Container execution of image debian:8" ;
    dct:type "Agent",
        "SoftwareAgent" ;
    cwlprov:image "debian:8" .

uuid:d7e8b17e-2d80-4c42-a797-bc3628f52c44 rdfs:label "Run of workflow/packed.cwl#main/sorted" ;
    dct:type "Activity",
        "wfprov:ProcessRun" ;
    prov:qualifiedAssociation [ dct:type "Association" ;
            prov:hadPlan <wf:main/sorted> ] ;
    prov:qualifiedEnd [ dct:type "End" ;
            prov:atTime "2018-10-25T15:46:38.069110"^^xsd:dateTime ;
            prov:hadActivity uuid:1f767ad4-ac52-4623-b5bc-dd9faf2b869f ] ;
    prov:qualifiedStart [ dct:type "Start" ;
            prov:atTime "2018-10-25T15:46:36.975235"^^xsd:dateTime ;
            prov:hadActivity uuid:1f767ad4-ac52-4623-b5bc-dd9faf2b869f ] ;
    prov:qualifiedUsage [ dct:type "Usage" ;
            prov:atTime "2018-10-25T15:46:37.067864"^^xsd:dateTime ;
            prov:entity uuid:4ab5a3fe-e481-4f7f-98c4-af8e5dfccb93 ],
        [ dct:type "Usage" ;
            prov:atTime "2018-10-25T15:46:37.067604"^^xsd:dateTime ;
            prov:entity uuid:feabfc2c-e5eb-49d0-ad5c-c19076482265 ] ;
    prov:wasAssociatedWith uuid:ac9c1653-4291-47bc-86f8-6dedcff13519,
        uuid:ba0fe122-124e-417b-8a2a-95e721320a2d .

uuid:ed8d007b-a1f3-4bfe-b390-08df074d712d dct:type "Entity" ;
    prov:value true .

uuid:f5ce6344-3b3b-4653-84fd-1f5abfa57fb0 rdfs:label "Container execution of image debian:8" ;
    dct:type "Agent",
        "SoftwareAgent" ;
    cwlprov:image "debian:8" .

uuid:f81dd60b-46db-4e58-b9f9-5606de1f10de rdfs:label "Run of workflow/packed.cwl#main/rev" ;
    dct:type "Activity",
        "wfprov:ProcessRun" ;
    prov:qualifiedAssociation [ dct:type "Association" ;
            prov:hadPlan <arcp://uuid,1f767ad4-ac52-4623-b5bc-dd9faf2b869f/workflow/packed.cwl#main/rev> ] ;
    prov:qualifiedEnd [ dct:type "End" ;
            prov:atTime "2018-10-25T15:46:36.967359"^^xsd:dateTime ;
            prov:hadActivity uuid:1f767ad4-ac52-4623-b5bc-dd9faf2b869f ] ;
    prov:qualifiedStart [ dct:type "Start" ;
            prov:atTime "2018-10-25T15:46:35.314101"^^xsd:dateTime ;
            prov:hadActivity uuid:1f767ad4-ac52-4623-b5bc-dd9faf2b869f ] ;
    prov:qualifiedUsage [ dct:type "Usage" ;
            prov:atTime "2018-10-25T15:46:35.597726"^^xsd:dateTime ;
            prov:entity uuid:6e84364f-faa9-4a27-aaba-5e4b80d9564b ] ;
    prov:wasAssociatedWith uuid:ac9c1653-4291-47bc-86f8-6dedcff13519,
        uuid:f5ce6344-3b3b-4653-84fd-1f5abfa57fb0 .

uuid:fe16801a-7995-4968-a8bb-5e9d46255bb7 dct:type "Entity",
        "wf4ever:File",
        "wfprov:Artifact" ;
    prov:specializationOf sha1:327fc7aedf4f6b69a42a7c8b808dc5a7aff61376 ;
    cwlprov:basename "whale.txt" ;
    cwlprov:nameext ".txt" ;
    cwlprov:nameroot "whale" .

uuid:feabfc2c-e5eb-49d0-ad5c-c19076482265 dct:type "Entity",
        "wf4ever:File",
        "wfprov:Artifact" ;
    prov:qualifiedGeneration [ dct:type "Generation" ;
            prov:activity uuid:f81dd60b-46db-4e58-b9f9-5606de1f10de ;
            prov:atTime "2018-10-25T15:46:36.963254"^^xsd:dateTime ] ;
    prov:specializationOf sha1:97fe1b50b4582cebc7d853796ebd62e3e163aa3f ;
    cwlprov:basename "output.txt" ;
    cwlprov:nameext ".txt" ;
    cwlprov:nameroot "output" .

<wf:main/sorted> dct:type "Entity",
        "Plan",
        "wfdesc:Process" .

<arcp://uuid,1f767ad4-ac52-4623-b5bc-dd9faf2b869f/workflow/packed.cwl#main/rev> dct:type "Entity",
        "Plan",
        "wfdesc:Process" .

sha1:327fc7aedf4f6b69a42a7c8b808dc5a7aff61376 dct:type "Entity",
        "wfprov:Artifact" .

uuid:1f767ad4-ac52-4623-b5bc-dd9faf2b869f rdfs:label "Run of workflow/packed.cwl#main" ;
    dct:type "Activity",
        "wfprov:WorkflowRun" ;
    prov:qualifiedAssociation [ dct:type "Association" ;
            prov:hadPlan wf:main ] ;
    prov:qualifiedEnd [ dct:type "End" ;
            prov:atTime "2018-10-25T15:46:43.020168"^^xsd:dateTime ;
            prov:hadActivity uuid:ac9c1653-4291-47bc-86f8-6dedcff13519 ] ;
    prov:qualifiedStart [ dct:type "Start" ;
            prov:atTime "2018-10-25T15:46:35.211153"^^xsd:dateTime ;
            prov:hadActivity uuid:ac9c1653-4291-47bc-86f8-6dedcff13519 ] ;
    prov:qualifiedUsage [ dct:type "Usage" ;
            prov:atTime "2018-10-25T15:46:35.303484"^^xsd:dateTime ;
            prov:entity uuid:fe16801a-7995-4968-a8bb-5e9d46255bb7 ],
        [ dct:type "Usage" ;
            prov:atTime "2018-10-25T15:46:35.303643"^^xsd:dateTime ;
            prov:entity uuid:ed8d007b-a1f3-4bfe-b390-08df074d712d ] ;
    prov:startedAtTime "2018-10-25T15:46:35.211026"^^xsd:dateTime ;
    prov:wasAssociatedWith uuid:ac9c1653-4291-47bc-86f8-6dedcff13519 .

uuid:ac9c1653-4291-47bc-86f8-6dedcff13519 rdfs:label "cwltool 1.0.20181012180214" ;
    dct:type "Agent",
        "SoftwareAgent",
        "wfprov:WorkflowEngine" ;
    prov:qualifiedStart [ dct:type "Start" ;
            prov:atTime "2018-10-25T15:46:35.210973"^^xsd:dateTime ;
            prov:hadActivity uuid:7fa2c8d0-9a3e-4512-9171-fc3b729c2210 ] .


```

<blockquote class="lang-specific turtle">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/ogcincubator/prov-cwl/master/build/tests/prov/template/example-prov-profile/example_2_1.ttl">Open in new window</a>
</blockquote>



## Profile example

JSON



```json
{
  "id": "uuid:071d1b5c-1b2b-4995-a6e0-80821af85abd",
  "type": [
    "Entity",
    "wf4ever:File",
    "wfprov:Artifact"
  ],
  "qualifiedGeneration": [
    {
      "type": "Generation",
      "activity": {
        "id": "uuid:d7e8b17e-2d80-4c42-a797-bc3628f52c44",
        "type": [
          "wfprov:ProcessRun",
          "Activity"
        ],
        "name": "Run of workflow/packed.cwl#main/sorted",
        "qualifiedAssociation": {
          "type": "Association",
          "hadPlan": {
            "id":" wf:main/sorted",
            "type": [
              "Entity",
              "Plan",
              "wfdesc:Process"
            ]
          }
        },
        "qualifiedEnd": {
          "type": "End",
          "atTime": "2018-10-25T15:46:38.069110",
          "hadActivity": {
            "id": "uuid:1f767ad4-ac52-4623-b5bc-dd9faf2b869f",
            "type": [
              "wfprov:WorkflowRun",
              "Activity"
            ],
            "name": "Run of workflow/packed.cwl#main",
            "qualifiedAssociation": {
              "type": "Association",
              "hadPlan": {
                "id": "wf:main",
                "type": [
                  "Entity",
                  "Plan",
                  "wfdesc:Workflow"
                ],
                "wfdesc:hasSubProcess": [
                  {
                    "id": "wf:main/rev",
                    "type": [
                      "Plan",
                      "Entity",
                      "wfdesc:Process"
                    ]
                  },
                  {
                    "id": "wf:main/sorted"
                  }
                ],
                "name": "Prospective provenance"
              }
            },
            "startedAtTime": "2018-10-25T15:46:35.211026",
            "wasAssociatedWith": "uuid:ac9c1653-4291-47bc-86f8-6dedcff13519"
          }
        }
      },
      "atTime": "2018-10-25T15:46:38.058365",
      "hadRole": "wf:main/sorted/output"
    },
    {
      "type": "Generation",
      "activity": "uuid:1f767ad4-ac52-4623-b5bc-dd9faf2b869f",
      "atTime": "2018-10-25T15:46:43.020002",
      "hadRole": "wf:main/primary/output"
    }
  ],
  "specializationOf": {
    "id": "sha1:b9214658cc453331b62c2282b772a5c063dbd284",
    "type": [
      "Entity",
      "wfprov:Artifact"
    ]
  },
  "cwlprov:basename": "output.txt",
  "cwlprov:nameext": ".txt",
  "cwlprov:nameroot": "output"
}
```

<blockquote class="lang-specific json">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/ogcincubator/prov-cwl/master/build/tests/prov/template/example-prov-profile/example_3_1.json">Open in new window</a>
    <a target="_blank" href="https://avillar.github.io/TreedocViewer/?dataParser=json&amp;dataUrl=https%3A%2F%2Fraw.githubusercontent.com%2Fogcincubator%2Fprov-cwl%2Fmaster%2Fbuild%2Ftests%2Fprov%2Ftemplate%2Fexample-prov-profile%2Fexample_3_1.json&amp;expand=2&amp;option=%7B%22showTable%22%3A+false%7D">View on JSON Viewer</a></p>
</blockquote>




```jsonld
{
  "id": "uuid:071d1b5c-1b2b-4995-a6e0-80821af85abd",
  "type": [
    "Entity",
    "wf4ever:File",
    "wfprov:Artifact"
  ],
  "qualifiedGeneration": [
    {
      "type": "Generation",
      "activity": {
        "id": "uuid:d7e8b17e-2d80-4c42-a797-bc3628f52c44",
        "type": [
          "wfprov:ProcessRun",
          "Activity"
        ],
        "name": "Run of workflow/packed.cwl#main/sorted",
        "qualifiedAssociation": {
          "type": "Association",
          "hadPlan": {
            "id": " wf:main/sorted",
            "type": [
              "Entity",
              "Plan",
              "wfdesc:Process"
            ]
          }
        },
        "qualifiedEnd": {
          "type": "End",
          "atTime": "2018-10-25T15:46:38.069110",
          "hadActivity": {
            "id": "uuid:1f767ad4-ac52-4623-b5bc-dd9faf2b869f",
            "type": [
              "wfprov:WorkflowRun",
              "Activity"
            ],
            "name": "Run of workflow/packed.cwl#main",
            "qualifiedAssociation": {
              "type": "Association",
              "hadPlan": {
                "id": "wf:main",
                "type": [
                  "Entity",
                  "Plan",
                  "wfdesc:Workflow"
                ],
                "wfdesc:hasSubProcess": [
                  {
                    "id": "wf:main/rev",
                    "type": [
                      "Plan",
                      "Entity",
                      "wfdesc:Process"
                    ]
                  },
                  {
                    "id": "wf:main/sorted"
                  }
                ],
                "name": "Prospective provenance"
              }
            },
            "startedAtTime": "2018-10-25T15:46:35.211026",
            "wasAssociatedWith": "uuid:ac9c1653-4291-47bc-86f8-6dedcff13519"
          }
        }
      },
      "atTime": "2018-10-25T15:46:38.058365",
      "hadRole": "wf:main/sorted/output"
    },
    {
      "type": "Generation",
      "activity": "uuid:1f767ad4-ac52-4623-b5bc-dd9faf2b869f",
      "atTime": "2018-10-25T15:46:43.020002",
      "hadRole": "wf:main/primary/output"
    }
  ],
  "specializationOf": {
    "id": "sha1:b9214658cc453331b62c2282b772a5c063dbd284",
    "type": [
      "Entity",
      "wfprov:Artifact"
    ]
  },
  "cwlprov:basename": "output.txt",
  "cwlprov:nameext": ".txt",
  "cwlprov:nameroot": "output",
  "@context": "https://raw.githubusercontent.com/ogcincubator/prov-cwl/master/build/annotated/prov/template/example-prov-profile/context.jsonld"
}
```

<blockquote class="lang-specific jsonld">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/ogcincubator/prov-cwl/master/build/tests/prov/template/example-prov-profile/example_3_1.jsonld">Open in new window</a>
    <a target="_blank" href="https://json-ld.org/playground/#json-ld=https%3A%2F%2Fraw.githubusercontent.com%2Fogcincubator%2Fprov-cwl%2Fmaster%2Fbuild%2Ftests%2Fprov%2Ftemplate%2Fexample-prov-profile%2Fexample_3_1.jsonld">View on JSON-LD Playground</a>
</blockquote>




```turtle
@prefix cwlprov: <https://w3id.org/cwl/prov#> .
@prefix dct: <http://purl.org/dc/terms/> .
@prefix prov: <http://www.w3.org/ns/prov#> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix sha1: <urn:hash::sha1:> .
@prefix uuid: <urn:uuid:> .
@prefix wf: <arcp://uuid,1f767ad4-ac52-4623-b5bc-dd9faf2b869f/workflow/packed.cwl#> .
@prefix wfdesc: <http://purl.org/wf4ever/wfdesc#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

uuid:071d1b5c-1b2b-4995-a6e0-80821af85abd dct:type "Entity",
        "wf4ever:File",
        "wfprov:Artifact" ;
    prov:qualifiedGeneration [ dct:type "Generation" ;
            prov:activity uuid:d7e8b17e-2d80-4c42-a797-bc3628f52c44 ;
            prov:atTime "2018-10-25T15:46:38.058365"^^xsd:dateTime ],
        [ dct:type "Generation" ;
            prov:activity uuid:1f767ad4-ac52-4623-b5bc-dd9faf2b869f ;
            prov:atTime "2018-10-25T15:46:43.020002"^^xsd:dateTime ] ;
    prov:specializationOf sha1:b9214658cc453331b62c2282b772a5c063dbd284 ;
    cwlprov:basename "output.txt" ;
    cwlprov:nameext ".txt" ;
    cwlprov:nameroot "output" .

wf:main rdfs:label "Prospective provenance" ;
    dct:type "Entity",
        "Plan",
        "wfdesc:Workflow" ;
    wfdesc:hasSubProcess <arcp://uuid,1f767ad4-ac52-4623-b5bc-dd9faf2b869f/workflow/packed.cwl#main/rev>,
        <arcp://uuid,1f767ad4-ac52-4623-b5bc-dd9faf2b869f/workflow/packed.cwl#main/sorted> .

<arcp://uuid,1f767ad4-ac52-4623-b5bc-dd9faf2b869f/workflow/packed.cwl#main/rev> dct:type "Entity",
        "Plan",
        "wfdesc:Process" .

sha1:b9214658cc453331b62c2282b772a5c063dbd284 dct:type "Entity",
        "wfprov:Artifact" .

uuid:d7e8b17e-2d80-4c42-a797-bc3628f52c44 rdfs:label "Run of workflow/packed.cwl#main/sorted" ;
    dct:type "Activity",
        "wfprov:ProcessRun" ;
    prov:qualifiedAssociation [ dct:type "Association" ;
            prov:hadPlan <wf:main/sorted> ] ;
    prov:qualifiedEnd [ dct:type "End" ;
            prov:atTime "2018-10-25T15:46:38.069110"^^xsd:dateTime ;
            prov:hadActivity uuid:1f767ad4-ac52-4623-b5bc-dd9faf2b869f ] .

<wf:main/sorted> dct:type "Entity",
        "Plan",
        "wfdesc:Process" .

uuid:1f767ad4-ac52-4623-b5bc-dd9faf2b869f rdfs:label "Run of workflow/packed.cwl#main" ;
    dct:type "Activity",
        "wfprov:WorkflowRun" ;
    prov:qualifiedAssociation [ dct:type "Association" ;
            prov:hadPlan wf:main ] ;
    prov:startedAtTime "2018-10-25T15:46:35.211026"^^xsd:dateTime ;
    prov:wasAssociatedWith uuid:ac9c1653-4291-47bc-86f8-6dedcff13519 .


```

<blockquote class="lang-specific turtle">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/ogcincubator/prov-cwl/master/build/tests/prov/template/example-prov-profile/example_3_1.ttl">Open in new window</a>
</blockquote>



# JSON Schema

```yaml--schema
$schema: https://json-schema.org/draft/2020-12/schema
description: provenance chain
$defs:
  objectref:
    $anchor: objectref
    $ref: https://opengeospatial.github.io/bblocks/annotated-schemas/ogc-utils/iri-or-curie/schema.json
  oneOrMoreObjectref:
    $ref: https://opengeospatial.github.io/bblocks/annotated-schemas/ogc-utils/iri-or-curie/schema.json#/$defs/MultipleOrObject
  curie:
    $ref: https://opengeospatial.github.io/bblocks/annotated-schemas/ogc-utils/iri-or-curie/schema.json
  oneOrMoreActivitiesOrRefIds:
    oneOf:
    - $ref: '#/$defs/objectref'
    - $ref: '#/$defs/Activity'
    - type: array
      items:
        anyOf:
        - $ref: '#/$defs/objectref'
        - $ref: '#/$defs/Activity'
  oneOrMoreEntitiesOrRefIds:
    oneOf:
    - $ref: '#/$defs/objectref'
    - $ref: '#/$defs/Entity'
    - type: array
      items:
        anyOf:
        - $ref: '#/$defs/objectref'
        - $ref: '#/$defs/Entity'
  oneOrMoreAgentsOrRefIds:
    oneOf:
    - $ref: '#/$defs/objectref'
    - $ref: '#/$defs/externalLink'
    - $ref: '#/$defs/Agent'
    - type: array
      items:
        anyOf:
        - $ref: '#/$defs/objectref'
        - $ref: '#/$defs/Agent'
  externalLink:
    $ref: https://opengeospatial.github.io/bblocks/annotated-schemas/ogc-utils/json-link/schema.json
  influenced:
    type: object
    properties:
      wasInfluencedBy:
        anyOf:
        - $ref: '#/$defs/oneOrMoreActivitiesOrRefIds'
        - $ref: '#/$defs/oneOrMoreEntitiesOrRefIds'
        - $ref: '#/$defs/oneOrMoreAgentsOrRefIds'
        x-jsonld-id: http://www.w3.org/ns/prov#wasInfluencedBy
        x-jsonld-type: '@id'
      qualifiedInfluence:
        oneOf:
        - $ref: '#/$defs/objectref'
        - $ref: '#/$defs/Influence'
        - type: array
          items:
            oneOf:
            - $ref: '#/$defs/objectref'
            - $ref: '#/$defs/Influence'
        x-jsonld-id: http://www.w3.org/ns/prov#qualifiedInfluence
        x-jsonld-type: '@id'
  Entity:
    type: object
    properties:
      id:
        $ref: '#/$defs/curie'
        x-jsonld-id: '@id'
      featureType:
        $ref: '#/$defs/objectref'
      provenance:
        $ref: '#/$defs/Prov'
      wasGeneratedBy:
        $ref: '#/$defs/oneOrMoreActivitiesOrRefIds'
        x-jsonld-id: http://www.w3.org/ns/prov#wasGeneratedBy
        x-jsonld-type: '@id'
      wasAttributedTo:
        $ref: '#/$defs/oneOrMoreAgentsOrRefIds'
        x-jsonld-id: http://www.w3.org/ns/prov#wasAttributedTo
        x-jsonld-type: '@id'
      wasDerivedFrom:
        $ref: '#/$defs/oneOrMoreEntitiesOrRefIds'
        x-jsonld-id: http://www.w3.org/ns/prov#wasDerivedFrom
        x-jsonld-type: '@id'
      alternateOf:
        $ref: '#/$defs/oneOrMoreEntitiesOrRefIds'
        x-jsonld-id: http://www.w3.org/ns/prov#alternateOf
        x-jsonld-type: '@id'
      hadPrimarySource:
        $ref: '#/$defs/oneOrMoreEntitiesOrRefIds'
        x-jsonld-id: http://www.w3.org/ns/prov#hadPrimarySource
        x-jsonld-type: '@id'
      specializationOf:
        $ref: '#/$defs/oneOrMoreEntitiesOrRefIds'
        x-jsonld-id: http://www.w3.org/ns/prov#specializationOf
        x-jsonld-type: '@id'
      wasInvalidatedBy:
        $ref: '#/$defs/oneOrMoreAgentsOrRefIds'
        x-jsonld-id: http://www.w3.org/ns/prov#wasInvalidatedBy
        x-jsonld-type: '@id'
      wasQuotedFrom:
        $ref: '#/$defs/oneOrMoreAgentsOrRefIds'
        x-jsonld-id: http://www.w3.org/ns/prov#wasQuotedFrom
        x-jsonld-type: '@id'
      wasRevisionOf:
        $ref: '#/$defs/oneOrMoreAgentsOrRefIds'
        x-jsonld-id: http://www.w3.org/ns/prov#wasRevisionOf
        x-jsonld-type: '@id'
      mentionOf:
        $ref: '#/$defs/oneOrMoreAgentsOrRefIds'
        x-jsonld-id: http://www.w3.org/ns/prov#mentionOf
        x-jsonld-type: '@id'
      atLocation:
        $ref: '#/$defs/objectref'
        x-jsonld-id: http://www.w3.org/ns/prov#atLocation
        x-jsonld-type: '@id'
      links:
        type: array
        items:
          $ref: '#/$defs/externalLink'
      qualifiedGeneration:
        oneOf:
        - $ref: '#/$defs/objectref'
        - $ref: '#/$defs/Generation'
        - type: array
          items:
            oneOf:
            - $ref: '#/$defs/objectref'
            - $ref: '#/$defs/Generation'
        x-jsonld-id: http://www.w3.org/ns/prov#qualifiedGeneration
        x-jsonld-type: '@id'
      qualifiedInvalidation:
        oneOf:
        - $ref: '#/$defs/objectref'
        - $ref: '#/$defs/Invalidation'
        - type: array
          items:
            oneOf:
            - $ref: '#/$defs/objectref'
            - $ref: '#/$defs/Invalidation'
        x-jsonld-id: http://www.w3.org/ns/prov#qualifiedInvalidation
        x-jsonld-type: '@id'
      qualifiedDerivation:
        oneOf:
        - $ref: '#/$defs/objectref'
        - $ref: '#/$defs/Derivation'
        - type: array
          items:
            oneOf:
            - $ref: '#/$defs/objectref'
            - $ref: '#/$defs/Derivation'
        x-jsonld-id: http://www.w3.org/ns/prov#qualifiedDerivation
        x-jsonld-type: '@id'
      qualifiedAttribution:
        oneOf:
        - $ref: '#/$defs/objectref'
        - $ref: '#/$defs/Attribution'
        - type: array
          items:
            oneOf:
            - $ref: '#/$defs/objectref'
            - $ref: '#/$defs/Attribution'
        x-jsonld-id: http://www.w3.org/ns/prov#qualifiedAttribution
        x-jsonld-type: '@id'
    required:
    - id
    anyOf:
    - properties:
        type:
          oneOf:
          - type: string
            enum:
            - Entity
            - Bundle
            - Plan
          - type: array
            contains:
              type: string
              enum:
              - Entity
              - Bundle
              - Plan
      required:
      - type
    - required:
      - featureType
    - required:
      - wasGeneratedBy
    - required:
      - wasAttributedTo
    - required:
      - wasDerivedFrom
    - required:
      - provenance
    - properties:
        type:
          type: string
          const: Collection
        hadMember:
          type: array
          items:
            $ref: '#/$defs/Entity'
          x-jsonld-id: http://www.w3.org/ns/prov#hadMember
          x-jsonld-type: '@id'
      required:
      - hadMember
      - type
    - properties:
        type:
          type: string
          const: EmptyCollection
        hadMember:
          type: array
          maxItems: 0
          x-jsonld-id: http://www.w3.org/ns/prov#hadMember
          x-jsonld-type: '@id'
      required:
      - hadMember
      - type
    allOf:
    - $ref: '#/$defs/influenced'
  dateTime:
    type: string
    format: date-time
    pattern: ^\d{4}-\d{2}-\d{2}T\d{2}:\d{2}:\d{2}(?:\.\d+)?(?:Z|[+-]\d{2}:\d{2})?$
  Activity:
    type: object
    properties:
      id:
        $ref: '#/$defs/curie'
        x-jsonld-id: '@id'
      type:
        $ref: '#/$defs/oneOrMoreObjectref'
      endedAtTime:
        $ref: '#/$defs/dateTime'
        x-jsonld-id: http://www.w3.org/ns/prov#endedAtTime
        x-jsonld-type: http://www.w3.org/2001/XMLSchema#dateTime
      wasAssociatedWith:
        $ref: '#/$defs/oneOrMoreAgentsOrRefIds'
        x-jsonld-id: http://www.w3.org/ns/prov#wasAssociatedWith
        x-jsonld-type: '@id'
      wasInformedBy:
        $ref: '#/$defs/oneOrMoreActivitiesOrRefIds'
        x-jsonld-id: http://www.w3.org/ns/prov#wasInformedBy
        x-jsonld-type: '@id'
      used:
        $ref: '#/$defs/oneOrMoreEntitiesOrRefIds'
        x-jsonld-id: http://www.w3.org/ns/prov#used
        x-jsonld-type: '@id'
      wasStartedBy:
        $ref: '#/$defs/oneOrMoreEntitiesOrRefIds'
        x-jsonld-id: http://www.w3.org/ns/prov#wasStartedBy
        x-jsonld-type: '@id'
      wasEndedBy:
        $ref: '#/$defs/oneOrMoreEntitiesOrRefIds'
        x-jsonld-id: http://www.w3.org/ns/prov#wasEndedBy
        x-jsonld-type: '@id'
      invalidated:
        $ref: '#/$defs/oneOrMoreEntitiesOrRefIds'
        x-jsonld-id: http://www.w3.org/ns/prov#invalidated
        x-jsonld-type: '@id'
      generated:
        $ref: '#/$defs/oneOrMoreEntitiesOrRefIds'
        x-jsonld-id: http://www.w3.org/ns/prov#generated
        x-jsonld-type: '@id'
      atLocation:
        $ref: '#/$defs/objectref'
        x-jsonld-id: http://www.w3.org/ns/prov#atLocation
        x-jsonld-type: '@id'
      qualifiedUsage:
        oneOf:
        - $ref: '#/$defs/objectref'
        - $ref: '#/$defs/Usage'
        - type: array
          items:
            oneOf:
            - $ref: '#/$defs/objectref'
            - $ref: '#/$defs/Usage'
        x-jsonld-id: http://www.w3.org/ns/prov#qualifiedUsage
        x-jsonld-type: '@id'
      qualifiedCommunication:
        oneOf:
        - $ref: '#/$defs/objectref'
        - $ref: '#/$defs/Communication'
        - type: array
          items:
            oneOf:
            - $ref: '#/$defs/objectref'
            - $ref: '#/$defs/Generation'
        x-jsonld-id: http://www.w3.org/ns/prov#qualifiedCommunication
        x-jsonld-type: '@id'
      qualifiedStart:
        oneOf:
        - $ref: '#/$defs/objectref'
        - $ref: '#/$defs/Start'
        x-jsonld-id: http://www.w3.org/ns/prov#qualifiedStart
        x-jsonld-type: '@id'
      qualifiedEnd:
        oneOf:
        - $ref: '#/$defs/objectref'
        - $ref: '#/$defs/End'
        x-jsonld-id: http://www.w3.org/ns/prov#qualifiedEnd
        x-jsonld-type: '@id'
      qualifiedAssociation:
        oneOf:
        - $ref: '#/$defs/objectref'
        - $ref: '#/$defs/Association'
        - type: array
          items:
            oneOf:
            - $ref: '#/$defs/objectref'
            - $ref: '#/$defs/Association'
        x-jsonld-id: http://www.w3.org/ns/prov#qualifiedAssociation
        x-jsonld-type: '@id'
    anyOf:
    - properties:
        type:
          oneOf:
          - type: string
            const: Activity
          - type: array
            contains:
              type: string
              const: Activity
            items:
              type: string
      required:
      - type
    - required:
      - activity
    - required:
      - used
    - required:
      - wasInformedBy
    - required:
      - endedAtTime
    - required:
      - startedAtTime
    - required:
      - wasAssociatedWith
    allOf:
    - $ref: '#/$defs/influenced'
  Agent:
    type: object
    properties:
      type:
        $ref: '#/$defs/oneOrMoreObjectref'
      name:
        type: string
        x-jsonld-id: http://www.w3.org/2000/01/rdf-schema#label
      id:
        $ref: '#/$defs/curie'
        x-jsonld-id: '@id'
      actedOnBehalfOf:
        $ref: '#/$defs/oneOrMoreAgentsOrRefIds'
        x-jsonld-id: http://www.w3.org/ns/prov#actedOnBehalfOf
        x-jsonld-type: '@id'
      atLocation:
        $ref: '#/$defs/objectref'
        x-jsonld-id: http://www.w3.org/ns/prov#atLocation
        x-jsonld-type: '@id'
      qualifiedDelegation:
        oneOf:
        - $ref: '#/$defs/objectref'
        - $ref: '#/$defs/Delegation'
        - type: array
          items:
            oneOf:
            - $ref: '#/$defs/objectref'
            - $ref: '#/$defs/Delegation'
        x-jsonld-id: http://www.w3.org/ns/prov#qualifiedDelegation
        x-jsonld-type: '@id'
    required:
    - name
    anyOf:
    - properties:
        type:
          oneOf:
          - type: string
            enum:
            - Agent
            - Organization
            - Person
            - SoftwareAgent
            - SoftwareDescription
            - DirectQueryService
          - type: array
            contains:
              type: string
              enum:
              - Agent
              - Organization
              - Person
              - SoftwareAgent
              - SoftwareDescription
              - DirectQueryService
            items:
              type: string
      required:
      - type
    - required:
      - agentType
    - required:
      - actedOnBehalfOf
    allOf:
    - $ref: '#/$defs/influenced'
  Usage:
    type: object
    properties:
      id:
        $ref: '#/$defs/curie'
        x-jsonld-id: '@id'
      type:
        oneOf:
        - type: string
          const: Usage
        - type: array
          contains:
            type: string
            const: Usage
          items:
            type: string
      atTime:
        $ref: '#/$defs/dateTime'
        x-jsonld-id: http://www.w3.org/ns/prov#atTime
        x-jsonld-type: http://www.w3.org/2001/XMLSchema#dateTime
      entity:
        oneOf:
        - $ref: '#/$defs/objectref'
        - $ref: '#/$defs/Entity'
        x-jsonld-id: http://www.w3.org/ns/prov#entity
        x-jsonld-type: '@id'
    required:
    - atTime
    - entity
  Generation:
    type: object
    properties:
      id:
        $ref: '#/$defs/curie'
        x-jsonld-id: '@id'
      type:
        oneOf:
        - type: string
          const: Generation
        - type: array
          contains:
            type: string
            const: Generation
          items:
            type: string
      atTime:
        $ref: '#/$defs/dateTime'
        x-jsonld-id: http://www.w3.org/ns/prov#atTime
        x-jsonld-type: http://www.w3.org/2001/XMLSchema#dateTime
      activity:
        oneOf:
        - $ref: '#/$defs/objectref'
        - $ref: '#/$defs/Activity'
        x-jsonld-id: http://www.w3.org/ns/prov#activity
        x-jsonld-type: '@id'
    required:
    - atTime
    - activity
  Invalidation:
    type: object
    properties:
      id:
        $ref: '#/$defs/curie'
        x-jsonld-id: '@id'
      type:
        oneOf:
        - type: string
          const: Invalidation
        - type: array
          contains:
            type: string
            const: Invalidation
          items:
            type: string
      atTime:
        $ref: '#/$defs/dateTime'
        x-jsonld-id: http://www.w3.org/ns/prov#atTime
        x-jsonld-type: http://www.w3.org/2001/XMLSchema#dateTime
      activity:
        oneOf:
        - $ref: '#/$defs/objectref'
        - $ref: '#/$defs/Activity'
        x-jsonld-id: http://www.w3.org/ns/prov#activity
        x-jsonld-type: '@id'
    required:
    - atTime
    - activity
  Communication:
    type: object
    properties:
      id:
        $ref: '#/$defs/curie'
        x-jsonld-id: '@id'
      type:
        oneOf:
        - type: string
          const: Communication
        - type: array
          contains:
            type: string
            const: Communication
          items:
            type: string
      activity:
        oneOf:
        - $ref: '#/$defs/objectref'
        - $ref: '#/$defs/Activity'
        x-jsonld-id: http://www.w3.org/ns/prov#activity
        x-jsonld-type: '@id'
    required:
    - activity
  StartOrEnd:
    type: object
    properties:
      id:
        $ref: '#/$defs/curie'
        x-jsonld-id: '@id'
      type:
        oneOf:
        - type: string
        - type: array
          items:
            type: string
      atTime:
        $ref: '#/$defs/dateTime'
        x-jsonld-id: http://www.w3.org/ns/prov#atTime
        x-jsonld-type: http://www.w3.org/2001/XMLSchema#dateTime
      entity:
        oneOf:
        - $ref: '#/$defs/objectref'
        - $ref: '#/$defs/Entity'
        x-jsonld-id: http://www.w3.org/ns/prov#entity
        x-jsonld-type: '@id'
      hadActivity:
        oneOf:
        - $ref: '#/$defs/objectref'
        - $ref: '#/$defs/Activity'
        x-jsonld-id: http://www.w3.org/ns/prov#hadActivity
        x-jsonld-type: '@id'
    required:
    - atTime
  Start:
    allOf:
    - $ref: '#/$defs/StartOrEnd'
    - properties:
        type:
          anyOf:
          - const: Start
          - contains:
              const: Start
  End:
    allOf:
    - $ref: '#/$defs/StartOrEnd'
    - properties:
        type:
          anyOf:
          - const: End
          - contains:
              const: End
  Derivation:
    type: object
    properties:
      id:
        $ref: '#/$defs/curie'
        x-jsonld-id: '@id'
      type:
        oneOf:
        - type: string
          const: Derivation
        - type: array
          contains:
            type: string
            const: Derivation
          items:
            type: string
      hadGeneration:
        oneOf:
        - $ref: '#/$defs/objectref'
        - $ref: '#/$defs/Generation'
        x-jsonld-id: http://www.w3.org/ns/prov#hadGeneration
        x-jsonld-type: '@id'
      hadActivity:
        oneOf:
        - $ref: '#/$defs/objectref'
        - $ref: '#/$defs/Activity'
        x-jsonld-id: http://www.w3.org/ns/prov#hadActivity
        x-jsonld-type: '@id'
      hadUsage:
        oneOf:
        - $ref: '#/$defs/objectref'
        - $ref: '#/$defs/Usage'
        x-jsonld-id: http://www.w3.org/ns/prov#hadUsage
        x-jsonld-type: '@id'
      entity:
        oneOf:
        - $ref: '#/$defs/objectref'
        - $ref: '#/$defs/Entity'
        x-jsonld-id: http://www.w3.org/ns/prov#entity
        x-jsonld-type: '@id'
    required:
    - atTime
    - entity
  Delegation:
    type: object
    properties:
      id:
        $ref: '#/$defs/curie'
        x-jsonld-id: '@id'
      type:
        oneOf:
        - type: string
          const: Delegation
        - type: array
          contains:
            type: string
            const: Delegation
          items:
            type: string
      agent:
        oneOf:
        - $ref: '#/$defs/objectref'
        - $ref: '#/$defs/Agent'
        x-jsonld-id: http://www.w3.org/ns/prov#agent
        x-jsonld-type: '@id'
      hadActivity:
        oneOf:
        - $ref: '#/$defs/objectref'
        - $ref: '#/$defs/Activity'
        x-jsonld-id: http://www.w3.org/ns/prov#hadActivity
        x-jsonld-type: '@id'
  Attribution:
    type: object
    properties:
      id:
        $ref: '#/$defs/curie'
        x-jsonld-id: '@id'
      type:
        oneOf:
        - type: string
          const: Attribution
        - type: array
          contains:
            type: string
            const: Attribution
          items:
            type: string
      agent:
        oneOf:
        - $ref: '#/$defs/objectref'
        - $ref: '#/$defs/Agent'
        x-jsonld-id: http://www.w3.org/ns/prov#agent
        x-jsonld-type: '@id'
  Association:
    type: object
    properties:
      id:
        $ref: '#/$defs/curie'
        x-jsonld-id: '@id'
      type:
        oneOf:
        - type: string
          const: Association
        - type: array
          contains:
            type: string
            const: Association
          items:
            type: string
      agent:
        oneOf:
        - $ref: '#/$defs/objectref'
        - $ref: '#/$defs/Agent'
        x-jsonld-id: http://www.w3.org/ns/prov#agent
        x-jsonld-type: '@id'
      hadRole:
        $ref: '#/$defs/oneOrMoreObjectref'
        x-jsonld-id: http://www.w3.org/ns/prov#hadRole
        x-jsonld-type: '@id'
      hadPlan:
        $ref: '#/$defs/oneOrMoreObjectref'
        x-jsonld-id: http://www.w3.org/ns/prov#hadPlan
        x-jsonld-type: '@id'
  Influence:
    type: object
    properties:
      id:
        $ref: '#/$defs/curie'
        x-jsonld-id: '@id'
      influencer:
        anyOf:
        - $ref: '#/$defs/oneOrMoreActivitiesOrRefIds'
        - $ref: '#/$defs/oneOrMoreEntitiesOrRefIds'
        - $ref: '#/$defs/oneOrMoreAgentsOrRefIds'
        x-jsonld-id: http://www.w3.org/ns/prov#influencer
        x-jsonld-type: '@id'
      entity:
        $ref: '#/$defs/oneOrMoreEntitiesOrRefIds'
        x-jsonld-id: http://www.w3.org/ns/prov#entity
        x-jsonld-type: '@id'
      activity:
        $ref: '#/$defs/oneOrMoreActivitiesOrRefIds'
        x-jsonld-id: http://www.w3.org/ns/prov#activity
        x-jsonld-type: '@id'
      agent:
        $ref: '#/$defs/oneOrMoreAgentsOrRefIds'
        x-jsonld-id: http://www.w3.org/ns/prov#agent
        x-jsonld-type: '@id'
    anyOf:
    - required:
      - influencer
    - required:
      - entity
    - required:
      - activity
    - required:
      - agent
  Prov:
    description: An list of provenance objects linked together to form a provenance
      chain for the current object. Objects may have nested objects as well, with
      or without referencable ids
    type: array
    items:
      oneOf:
      - $ref: '#/$defs/Entity'
      - $ref: '#/$defs/Activity'
      - $ref: '#/$defs/Agent'
anyOf:
- $ref: '#/$defs/Entity'
- $ref: '#/$defs/Activity'
x-jsonld-extra-terms:
  Activity: http://www.w3.org/ns/prov#Activity
  ActivityInfluence: http://www.w3.org/ns/prov#ActivityInfluence
  Agent: http://www.w3.org/ns/prov#Agent
  AgentInfluence: http://www.w3.org/ns/prov#AgentInfluence
  Association: http://www.w3.org/ns/prov#Association
  Attribution: http://www.w3.org/ns/prov#Attribution
  Bundle: http://www.w3.org/ns/prov#Bundle
  Collection: http://www.w3.org/ns/prov#Collection
  Communication: http://www.w3.org/ns/prov#Communication
  Delegation: http://www.w3.org/ns/prov#Delegation
  Derivation: http://www.w3.org/ns/prov#Derivation
  EmptyCollection: http://www.w3.org/ns/prov#EmptyCollection
  End: http://www.w3.org/ns/prov#End
  Entity: http://www.w3.org/ns/prov#Entity
  EntityInfluence: http://www.w3.org/ns/prov#EntityInfluence
  Generation: http://www.w3.org/ns/prov#Generation
  Influence: http://www.w3.org/ns/prov#Influence
  InstantaneousEvent: http://www.w3.org/ns/prov#InstantaneousEvent
  Invalidation: http://www.w3.org/ns/prov#Invalidation
  Location: http://www.w3.org/ns/prov#Location
  Organization: http://www.w3.org/ns/prov#Organization
  Person: http://www.w3.org/ns/prov#Person
  Plan: http://www.w3.org/ns/prov#Plan
  PrimarySource: http://www.w3.org/ns/prov#PrimarySource
  Quotation: http://www.w3.org/ns/prov#Quotation
  Revision: http://www.w3.org/ns/prov#Revision
  Role: http://www.w3.org/ns/prov#Role
  SoftwareAgent: http://www.w3.org/ns/prov#SoftwareAgent
  Start: http://www.w3.org/ns/prov#Start
  Usage: http://www.w3.org/ns/prov#Usage
  ServiceDescription: http://www.w3.org/ns/prov#ServiceDescription
  DirectQueryService: http://www.w3.org/ns/prov#DirectQueryService
  Accept: http://www.w3.org/ns/prov#Accept
  Contribute: http://www.w3.org/ns/prov#Contribute
  Contributor: http://www.w3.org/ns/prov#Contributor
  Copyright: http://www.w3.org/ns/prov#Copyright
  Create: http://www.w3.org/ns/prov#Create
  Creator: http://www.w3.org/ns/prov#Creator
  Modify: http://www.w3.org/ns/prov#Modify
  Publish: http://www.w3.org/ns/prov#Publish
  Publisher: http://www.w3.org/ns/prov#Publisher
  Replace: http://www.w3.org/ns/prov#Replace
  RightsAssignment: http://www.w3.org/ns/prov#RightsAssignment
  RightsHolder: http://www.w3.org/ns/prov#RightsHolder
  Submit: http://www.w3.org/ns/prov#Submit
  Dictionary: http://www.w3.org/ns/prov#Dictionary
  EmptyDictionary: http://www.w3.org/ns/prov#EmptyDictionary
  KeyEntityPair: http://www.w3.org/ns/prov#KeyEntityPair
  Insertion: http://www.w3.org/ns/prov#Insertion
  Removal: http://www.w3.org/ns/prov#Removal
  generatedAtTime:
    x-jsonld-id: http://www.w3.org/ns/prov#generatedAtTime
    x-jsonld-type: http://www.w3.org/2001/XMLSchema#dateTime
  invalidatedAtTime:
    x-jsonld-id: http://www.w3.org/ns/prov#invalidatedAtTime
    x-jsonld-type: http://www.w3.org/2001/XMLSchema#dateTime
  startedAtTime:
    x-jsonld-id: http://www.w3.org/ns/prov#startedAtTime
    x-jsonld-type: http://www.w3.org/2001/XMLSchema#dateTime
  value: http://www.w3.org/ns/prov#value
  provenanceUriTemplate: http://www.w3.org/ns/prov#provenanceUriTemplate
  pairKey:
    x-jsonld-id: http://www.w3.org/ns/prov#pairKey
    x-jsonld-type: http://www.w3.org/2000/01/rdf-schema#Literal
  removedKey:
    x-jsonld-id: http://www.w3.org/ns/prov#removedKey
    x-jsonld-type: http://www.w3.org/2000/01/rdf-schema#Literal
  influenced:
    x-jsonld-id: http://www.w3.org/ns/prov#influenced
    x-jsonld-type: '@id'
  qualifiedPrimarySource:
    x-jsonld-id: http://www.w3.org/ns/prov#qualifiedPrimarySource
    x-jsonld-type: '@id'
  qualifiedQuotation:
    x-jsonld-id: http://www.w3.org/ns/prov#qualifiedQuotation
    x-jsonld-type: '@id'
  qualifiedRevision:
    x-jsonld-id: http://www.w3.org/ns/prov#qualifiedRevision
    x-jsonld-type: '@id'
  has_anchor:
    x-jsonld-id: http://www.w3.org/ns/prov#has_anchor
    x-jsonld-type: '@id'
  has_provenance:
    x-jsonld-id: http://www.w3.org/ns/prov#has_provenance
    x-jsonld-type: '@id'
  has_query_service:
    x-jsonld-id: http://www.w3.org/ns/prov#has_query_service
    x-jsonld-type: '@id'
  describesService:
    x-jsonld-id: http://www.w3.org/ns/prov#describesService
    x-jsonld-type: '@id'
  pingback:
    x-jsonld-id: http://www.w3.org/ns/prov#pingback
    x-jsonld-type: '@id'
  dictionary:
    x-jsonld-id: http://www.w3.org/ns/prov#dictionary
    x-jsonld-type: '@id'
  derivedByInsertionFrom:
    x-jsonld-id: http://www.w3.org/ns/prov#derivedByInsertionFrom
    x-jsonld-type: '@id'
  derivedByRemovalFrom:
    x-jsonld-id: http://www.w3.org/ns/prov#derivedByRemovalFrom
    x-jsonld-type: '@id'
  insertedKeyEntityPair:
    x-jsonld-id: http://www.w3.org/ns/prov#insertedKeyEntityPair
    x-jsonld-type: '@id'
  hadDictionaryMember:
    x-jsonld-id: http://www.w3.org/ns/prov#hadDictionaryMember
    x-jsonld-type: '@id'
  pairEntity:
    x-jsonld-id: http://www.w3.org/ns/prov#pairEntity
    x-jsonld-type: '@id'
  qualifiedInsertion:
    x-jsonld-id: http://www.w3.org/ns/prov#qualifiedInsertion
    x-jsonld-type: '@id'
  qualifiedRemoval:
    x-jsonld-id: http://www.w3.org/ns/prov#qualifiedRemoval
    x-jsonld-type: '@id'
  asInBundle:
    x-jsonld-id: http://www.w3.org/ns/prov#asInBundle
    x-jsonld-type: '@id'
x-jsonld-prefixes:
  prov: http://www.w3.org/ns/prov#
  xsd: http://www.w3.org/2001/XMLSchema#
  rdfs: http://www.w3.org/2000/01/rdf-schema#
  rdf: http://www.w3.org/1999/02/22-rdf-syntax-ns#
  owl: http://www.w3.org/2002/07/owl#
  uuid: 'urn:uuid:'
  sha1: 'urn:hash::sha1:'
  wf: arcp://uuid,1f767ad4-ac52-4623-b5bc-dd9faf2b869f/workflow/packed.cwl#
  wf4ever: http://purl.org/wf4ever/wf4ever#
  wfdesc: http://purl.org/wf4ever/wfdesc#
  wfprov: http://purl.org/wf4ever/wfprov#
  cwlprov: https://w3id.org/cwl/prov#
  schemaorg: http://schema.org/
  foaf: http://xmlns.com/foaf/0.1/

```

> <a target="_blank" href="https://avillar.github.io/TreedocViewer/?dataParser=yaml&amp;dataUrl=https%3A%2F%2Fraw.githubusercontent.com%2Fogcincubator%2Fprov-cwl%2Fmaster%2Fbuild%2Fannotated%2Fprov%2Ftemplate%2Fexample-prov-profile%2Fschema.yaml&amp;expand=2&amp;option=%7B%22showTable%22%3A+false%7D">View on YAML Viewer</a>

Links to the schema:

* YAML version: <a href="https://raw.githubusercontent.com/ogcincubator/prov-cwl/master/build/annotated/prov/template/example-prov-profile/schema.yaml" target="_blank">https://raw.githubusercontent.com/ogcincubator/prov-cwl/master/build/annotated/prov/template/example-prov-profile/schema.yaml</a>
* JSON version: <a href="https://raw.githubusercontent.com/ogcincubator/prov-cwl/master/build/annotated/prov/template/example-prov-profile/schema.json" target="_blank">https://raw.githubusercontent.com/ogcincubator/prov-cwl/master/build/annotated/prov/template/example-prov-profile/schema.json</a>


# JSON-LD Context

```json--ldContext
{
  "@context": {
    "id": "@id",
    "endedAtTime": {
      "@id": "prov:endedAtTime",
      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
    },
    "wasAssociatedWith": {
      "@id": "prov:wasAssociatedWith",
      "@type": "@id",
      "@context": {
        "actedOnBehalfOf": {
          "@id": "prov:actedOnBehalfOf",
          "@type": "@id"
        },
        "qualifiedDelegation": {
          "@id": "prov:qualifiedDelegation",
          "@type": "@id",
          "@context": {
            "agent": {
              "@id": "prov:agent",
              "@type": "@id"
            },
            "hadActivity": {
              "@id": "prov:hadActivity",
              "@type": "@id"
            }
          }
        },
        "wasInfluencedBy": {
          "@id": "prov:wasInfluencedBy",
          "@type": "@id",
          "@context": {
            "wasGeneratedBy": {
              "@id": "prov:wasGeneratedBy",
              "@type": "@id"
            },
            "wasAttributedTo": {
              "@id": "prov:wasAttributedTo",
              "@type": "@id"
            },
            "wasInvalidatedBy": {
              "@id": "prov:wasInvalidatedBy",
              "@type": "@id"
            },
            "wasQuotedFrom": {
              "@id": "prov:wasQuotedFrom",
              "@type": "@id"
            },
            "wasRevisionOf": {
              "@id": "prov:wasRevisionOf",
              "@type": "@id"
            },
            "mentionOf": {
              "@id": "prov:mentionOf",
              "@type": "@id"
            },
            "qualifiedGeneration": {
              "@id": "prov:qualifiedGeneration",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedInvalidation": {
              "@id": "prov:qualifiedInvalidation",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedDerivation": {
              "@id": "prov:qualifiedDerivation",
              "@type": "@id",
              "@context": {
                "hadGeneration": {
                  "@id": "prov:hadGeneration",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    }
                  }
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                },
                "hadUsage": {
                  "@id": "prov:hadUsage",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    }
                  }
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedAttribution": {
              "@id": "prov:qualifiedAttribution",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              }
            },
            "hadMember": {
              "@id": "prov:hadMember",
              "@type": "@id",
              "@context": {
                "hadMember": {
                  "@id": "prov:hadMember",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "qualifiedInfluence": {
          "@id": "prov:qualifiedInfluence",
          "@type": "@id",
          "@context": {
            "influencer": {
              "@id": "prov:influencer",
              "@type": "@id",
              "@context": {
                "wasGeneratedBy": {
                  "@id": "prov:wasGeneratedBy",
                  "@type": "@id"
                },
                "wasAttributedTo": {
                  "@id": "prov:wasAttributedTo",
                  "@type": "@id"
                },
                "wasInvalidatedBy": {
                  "@id": "prov:wasInvalidatedBy",
                  "@type": "@id"
                },
                "wasQuotedFrom": {
                  "@id": "prov:wasQuotedFrom",
                  "@type": "@id"
                },
                "wasRevisionOf": {
                  "@id": "prov:wasRevisionOf",
                  "@type": "@id"
                },
                "mentionOf": {
                  "@id": "prov:mentionOf",
                  "@type": "@id"
                },
                "qualifiedGeneration": {
                  "@id": "prov:qualifiedGeneration",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    }
                  }
                },
                "qualifiedInvalidation": {
                  "@id": "prov:qualifiedInvalidation",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    }
                  }
                },
                "qualifiedDerivation": {
                  "@id": "prov:qualifiedDerivation",
                  "@type": "@id",
                  "@context": {
                    "hadGeneration": {
                      "@id": "prov:hadGeneration",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        }
                      }
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    },
                    "hadUsage": {
                      "@id": "prov:hadUsage",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        }
                      }
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedAttribution": {
                  "@id": "prov:qualifiedAttribution",
                  "@type": "@id",
                  "@context": {}
                },
                "hadMember": {
                  "@id": "prov:hadMember",
                  "@type": "@id",
                  "@context": {
                    "hadMember": {
                      "@id": "prov:hadMember",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "entity": {
              "@id": "prov:entity",
              "@type": "@id",
              "@context": {
                "wasGeneratedBy": {
                  "@id": "prov:wasGeneratedBy",
                  "@type": "@id"
                },
                "wasAttributedTo": {
                  "@id": "prov:wasAttributedTo",
                  "@type": "@id"
                },
                "wasInvalidatedBy": {
                  "@id": "prov:wasInvalidatedBy",
                  "@type": "@id"
                },
                "wasQuotedFrom": {
                  "@id": "prov:wasQuotedFrom",
                  "@type": "@id"
                },
                "wasRevisionOf": {
                  "@id": "prov:wasRevisionOf",
                  "@type": "@id"
                },
                "mentionOf": {
                  "@id": "prov:mentionOf",
                  "@type": "@id"
                },
                "qualifiedGeneration": {
                  "@id": "prov:qualifiedGeneration",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    }
                  }
                },
                "qualifiedInvalidation": {
                  "@id": "prov:qualifiedInvalidation",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    }
                  }
                },
                "qualifiedDerivation": {
                  "@id": "prov:qualifiedDerivation",
                  "@type": "@id",
                  "@context": {
                    "hadGeneration": {
                      "@id": "prov:hadGeneration",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        }
                      }
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    },
                    "hadUsage": {
                      "@id": "prov:hadUsage",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        }
                      }
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedAttribution": {
                  "@id": "prov:qualifiedAttribution",
                  "@type": "@id",
                  "@context": {}
                },
                "hadMember": {
                  "@id": "prov:hadMember",
                  "@type": "@id",
                  "@context": {
                    "hadMember": {
                      "@id": "prov:hadMember",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "activity": {
              "@id": "prov:activity",
              "@type": "@id"
            },
            "agent": {
              "@id": "prov:agent",
              "@type": "@id"
            }
          }
        }
      }
    },
    "wasInformedBy": {
      "@id": "prov:wasInformedBy",
      "@type": "@id"
    },
    "used": {
      "@id": "prov:used",
      "@type": "@id",
      "@context": {
        "qualifiedDelegation": {
          "@id": "prov:qualifiedDelegation",
          "@type": "@id",
          "@context": {
            "agent": {
              "@id": "prov:agent",
              "@type": "@id"
            },
            "hadActivity": {
              "@id": "prov:hadActivity",
              "@type": "@id"
            }
          }
        },
        "wasInfluencedBy": {
          "@id": "prov:wasInfluencedBy",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            }
          }
        },
        "qualifiedInfluence": {
          "@id": "prov:qualifiedInfluence",
          "@type": "@id",
          "@context": {
            "influencer": {
              "@id": "prov:influencer",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                }
              }
            },
            "entity": {
              "@id": "prov:entity",
              "@type": "@id"
            },
            "activity": {
              "@id": "prov:activity",
              "@type": "@id"
            },
            "agent": {
              "@id": "prov:agent",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "wasGeneratedBy": {
          "@id": "prov:wasGeneratedBy",
          "@type": "@id"
        },
        "wasAttributedTo": {
          "@id": "prov:wasAttributedTo",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id"
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "wasInvalidatedBy": {
          "@id": "prov:wasInvalidatedBy",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id"
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "wasQuotedFrom": {
          "@id": "prov:wasQuotedFrom",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id"
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "wasRevisionOf": {
          "@id": "prov:wasRevisionOf",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id"
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "mentionOf": {
          "@id": "prov:mentionOf",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id"
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "qualifiedGeneration": {
          "@id": "prov:qualifiedGeneration",
          "@type": "@id",
          "@context": {
            "atTime": {
              "@id": "prov:atTime",
              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
            },
            "activity": {
              "@id": "prov:activity",
              "@type": "@id"
            }
          }
        },
        "qualifiedInvalidation": {
          "@id": "prov:qualifiedInvalidation",
          "@type": "@id",
          "@context": {
            "atTime": {
              "@id": "prov:atTime",
              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
            },
            "activity": {
              "@id": "prov:activity",
              "@type": "@id"
            }
          }
        },
        "qualifiedDerivation": {
          "@id": "prov:qualifiedDerivation",
          "@type": "@id",
          "@context": {
            "hadGeneration": {
              "@id": "prov:hadGeneration",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                }
              }
            },
            "hadActivity": {
              "@id": "prov:hadActivity",
              "@type": "@id"
            },
            "hadUsage": {
              "@id": "prov:hadUsage",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                }
              }
            },
            "entity": {
              "@id": "prov:entity",
              "@type": "@id"
            }
          }
        },
        "qualifiedAttribution": {
          "@id": "prov:qualifiedAttribution",
          "@type": "@id",
          "@context": {
            "agent": {
              "@id": "prov:agent",
              "@type": "@id",
              "@context": {
                "wasInfluencedBy": {
                  "@id": "prov:wasInfluencedBy",
                  "@type": "@id",
                  "@context": {}
                },
                "qualifiedInfluence": {
                  "@id": "prov:qualifiedInfluence",
                  "@type": "@id",
                  "@context": {
                    "influencer": {
                      "@id": "prov:influencer",
                      "@type": "@id",
                      "@context": {}
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    },
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id",
                      "@context": {}
                    }
                  }
                }
              }
            }
          }
        },
        "hadMember": {
          "@id": "prov:hadMember",
          "@type": "@id",
          "@context": {
            "hadMember": {
              "@id": "prov:hadMember",
              "@type": "@id"
            }
          }
        }
      }
    },
    "wasStartedBy": {
      "@id": "prov:wasStartedBy",
      "@type": "@id",
      "@context": {
        "qualifiedDelegation": {
          "@id": "prov:qualifiedDelegation",
          "@type": "@id",
          "@context": {
            "agent": {
              "@id": "prov:agent",
              "@type": "@id"
            },
            "hadActivity": {
              "@id": "prov:hadActivity",
              "@type": "@id"
            }
          }
        },
        "wasInfluencedBy": {
          "@id": "prov:wasInfluencedBy",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            }
          }
        },
        "qualifiedInfluence": {
          "@id": "prov:qualifiedInfluence",
          "@type": "@id",
          "@context": {
            "influencer": {
              "@id": "prov:influencer",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                }
              }
            },
            "entity": {
              "@id": "prov:entity",
              "@type": "@id"
            },
            "activity": {
              "@id": "prov:activity",
              "@type": "@id"
            },
            "agent": {
              "@id": "prov:agent",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "wasGeneratedBy": {
          "@id": "prov:wasGeneratedBy",
          "@type": "@id"
        },
        "wasAttributedTo": {
          "@id": "prov:wasAttributedTo",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id"
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "wasInvalidatedBy": {
          "@id": "prov:wasInvalidatedBy",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id"
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "wasQuotedFrom": {
          "@id": "prov:wasQuotedFrom",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id"
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "wasRevisionOf": {
          "@id": "prov:wasRevisionOf",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id"
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "mentionOf": {
          "@id": "prov:mentionOf",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id"
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "qualifiedGeneration": {
          "@id": "prov:qualifiedGeneration",
          "@type": "@id",
          "@context": {
            "atTime": {
              "@id": "prov:atTime",
              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
            },
            "activity": {
              "@id": "prov:activity",
              "@type": "@id"
            }
          }
        },
        "qualifiedInvalidation": {
          "@id": "prov:qualifiedInvalidation",
          "@type": "@id",
          "@context": {
            "atTime": {
              "@id": "prov:atTime",
              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
            },
            "activity": {
              "@id": "prov:activity",
              "@type": "@id"
            }
          }
        },
        "qualifiedDerivation": {
          "@id": "prov:qualifiedDerivation",
          "@type": "@id",
          "@context": {
            "hadGeneration": {
              "@id": "prov:hadGeneration",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                }
              }
            },
            "hadActivity": {
              "@id": "prov:hadActivity",
              "@type": "@id"
            },
            "hadUsage": {
              "@id": "prov:hadUsage",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                }
              }
            },
            "entity": {
              "@id": "prov:entity",
              "@type": "@id"
            }
          }
        },
        "qualifiedAttribution": {
          "@id": "prov:qualifiedAttribution",
          "@type": "@id",
          "@context": {
            "agent": {
              "@id": "prov:agent",
              "@type": "@id",
              "@context": {
                "wasInfluencedBy": {
                  "@id": "prov:wasInfluencedBy",
                  "@type": "@id",
                  "@context": {}
                },
                "qualifiedInfluence": {
                  "@id": "prov:qualifiedInfluence",
                  "@type": "@id",
                  "@context": {
                    "influencer": {
                      "@id": "prov:influencer",
                      "@type": "@id",
                      "@context": {}
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    },
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id",
                      "@context": {}
                    }
                  }
                }
              }
            }
          }
        },
        "hadMember": {
          "@id": "prov:hadMember",
          "@type": "@id",
          "@context": {
            "hadMember": {
              "@id": "prov:hadMember",
              "@type": "@id"
            }
          }
        }
      }
    },
    "wasEndedBy": {
      "@id": "prov:wasEndedBy",
      "@type": "@id",
      "@context": {
        "qualifiedDelegation": {
          "@id": "prov:qualifiedDelegation",
          "@type": "@id",
          "@context": {
            "agent": {
              "@id": "prov:agent",
              "@type": "@id"
            },
            "hadActivity": {
              "@id": "prov:hadActivity",
              "@type": "@id"
            }
          }
        },
        "wasInfluencedBy": {
          "@id": "prov:wasInfluencedBy",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            }
          }
        },
        "qualifiedInfluence": {
          "@id": "prov:qualifiedInfluence",
          "@type": "@id",
          "@context": {
            "influencer": {
              "@id": "prov:influencer",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                }
              }
            },
            "entity": {
              "@id": "prov:entity",
              "@type": "@id"
            },
            "activity": {
              "@id": "prov:activity",
              "@type": "@id"
            },
            "agent": {
              "@id": "prov:agent",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "wasGeneratedBy": {
          "@id": "prov:wasGeneratedBy",
          "@type": "@id"
        },
        "wasAttributedTo": {
          "@id": "prov:wasAttributedTo",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id"
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "wasInvalidatedBy": {
          "@id": "prov:wasInvalidatedBy",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id"
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "wasQuotedFrom": {
          "@id": "prov:wasQuotedFrom",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id"
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "wasRevisionOf": {
          "@id": "prov:wasRevisionOf",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id"
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "mentionOf": {
          "@id": "prov:mentionOf",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id"
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "qualifiedGeneration": {
          "@id": "prov:qualifiedGeneration",
          "@type": "@id",
          "@context": {
            "atTime": {
              "@id": "prov:atTime",
              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
            },
            "activity": {
              "@id": "prov:activity",
              "@type": "@id"
            }
          }
        },
        "qualifiedInvalidation": {
          "@id": "prov:qualifiedInvalidation",
          "@type": "@id",
          "@context": {
            "atTime": {
              "@id": "prov:atTime",
              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
            },
            "activity": {
              "@id": "prov:activity",
              "@type": "@id"
            }
          }
        },
        "qualifiedDerivation": {
          "@id": "prov:qualifiedDerivation",
          "@type": "@id",
          "@context": {
            "hadGeneration": {
              "@id": "prov:hadGeneration",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                }
              }
            },
            "hadActivity": {
              "@id": "prov:hadActivity",
              "@type": "@id"
            },
            "hadUsage": {
              "@id": "prov:hadUsage",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                }
              }
            },
            "entity": {
              "@id": "prov:entity",
              "@type": "@id"
            }
          }
        },
        "qualifiedAttribution": {
          "@id": "prov:qualifiedAttribution",
          "@type": "@id",
          "@context": {
            "agent": {
              "@id": "prov:agent",
              "@type": "@id",
              "@context": {
                "wasInfluencedBy": {
                  "@id": "prov:wasInfluencedBy",
                  "@type": "@id",
                  "@context": {}
                },
                "qualifiedInfluence": {
                  "@id": "prov:qualifiedInfluence",
                  "@type": "@id",
                  "@context": {
                    "influencer": {
                      "@id": "prov:influencer",
                      "@type": "@id",
                      "@context": {}
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    },
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id",
                      "@context": {}
                    }
                  }
                }
              }
            }
          }
        },
        "hadMember": {
          "@id": "prov:hadMember",
          "@type": "@id",
          "@context": {
            "hadMember": {
              "@id": "prov:hadMember",
              "@type": "@id"
            }
          }
        }
      }
    },
    "invalidated": {
      "@id": "prov:invalidated",
      "@type": "@id",
      "@context": {
        "qualifiedDelegation": {
          "@id": "prov:qualifiedDelegation",
          "@type": "@id",
          "@context": {
            "agent": {
              "@id": "prov:agent",
              "@type": "@id"
            },
            "hadActivity": {
              "@id": "prov:hadActivity",
              "@type": "@id"
            }
          }
        },
        "wasInfluencedBy": {
          "@id": "prov:wasInfluencedBy",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            }
          }
        },
        "qualifiedInfluence": {
          "@id": "prov:qualifiedInfluence",
          "@type": "@id",
          "@context": {
            "influencer": {
              "@id": "prov:influencer",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                }
              }
            },
            "entity": {
              "@id": "prov:entity",
              "@type": "@id"
            },
            "activity": {
              "@id": "prov:activity",
              "@type": "@id"
            },
            "agent": {
              "@id": "prov:agent",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "wasGeneratedBy": {
          "@id": "prov:wasGeneratedBy",
          "@type": "@id"
        },
        "wasAttributedTo": {
          "@id": "prov:wasAttributedTo",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id"
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "wasInvalidatedBy": {
          "@id": "prov:wasInvalidatedBy",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id"
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "wasQuotedFrom": {
          "@id": "prov:wasQuotedFrom",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id"
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "wasRevisionOf": {
          "@id": "prov:wasRevisionOf",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id"
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "mentionOf": {
          "@id": "prov:mentionOf",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id"
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "qualifiedGeneration": {
          "@id": "prov:qualifiedGeneration",
          "@type": "@id",
          "@context": {
            "atTime": {
              "@id": "prov:atTime",
              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
            },
            "activity": {
              "@id": "prov:activity",
              "@type": "@id"
            }
          }
        },
        "qualifiedInvalidation": {
          "@id": "prov:qualifiedInvalidation",
          "@type": "@id",
          "@context": {
            "atTime": {
              "@id": "prov:atTime",
              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
            },
            "activity": {
              "@id": "prov:activity",
              "@type": "@id"
            }
          }
        },
        "qualifiedDerivation": {
          "@id": "prov:qualifiedDerivation",
          "@type": "@id",
          "@context": {
            "hadGeneration": {
              "@id": "prov:hadGeneration",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                }
              }
            },
            "hadActivity": {
              "@id": "prov:hadActivity",
              "@type": "@id"
            },
            "hadUsage": {
              "@id": "prov:hadUsage",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                }
              }
            },
            "entity": {
              "@id": "prov:entity",
              "@type": "@id"
            }
          }
        },
        "qualifiedAttribution": {
          "@id": "prov:qualifiedAttribution",
          "@type": "@id",
          "@context": {
            "agent": {
              "@id": "prov:agent",
              "@type": "@id",
              "@context": {
                "wasInfluencedBy": {
                  "@id": "prov:wasInfluencedBy",
                  "@type": "@id",
                  "@context": {}
                },
                "qualifiedInfluence": {
                  "@id": "prov:qualifiedInfluence",
                  "@type": "@id",
                  "@context": {
                    "influencer": {
                      "@id": "prov:influencer",
                      "@type": "@id",
                      "@context": {}
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    },
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id",
                      "@context": {}
                    }
                  }
                }
              }
            }
          }
        },
        "hadMember": {
          "@id": "prov:hadMember",
          "@type": "@id",
          "@context": {
            "hadMember": {
              "@id": "prov:hadMember",
              "@type": "@id"
            }
          }
        }
      }
    },
    "generated": {
      "@id": "prov:generated",
      "@type": "@id",
      "@context": {
        "qualifiedDelegation": {
          "@id": "prov:qualifiedDelegation",
          "@type": "@id",
          "@context": {
            "agent": {
              "@id": "prov:agent",
              "@type": "@id"
            },
            "hadActivity": {
              "@id": "prov:hadActivity",
              "@type": "@id"
            }
          }
        },
        "wasInfluencedBy": {
          "@id": "prov:wasInfluencedBy",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            }
          }
        },
        "qualifiedInfluence": {
          "@id": "prov:qualifiedInfluence",
          "@type": "@id",
          "@context": {
            "influencer": {
              "@id": "prov:influencer",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                }
              }
            },
            "entity": {
              "@id": "prov:entity",
              "@type": "@id"
            },
            "activity": {
              "@id": "prov:activity",
              "@type": "@id"
            },
            "agent": {
              "@id": "prov:agent",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "wasGeneratedBy": {
          "@id": "prov:wasGeneratedBy",
          "@type": "@id"
        },
        "wasAttributedTo": {
          "@id": "prov:wasAttributedTo",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id"
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "wasInvalidatedBy": {
          "@id": "prov:wasInvalidatedBy",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id"
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "wasQuotedFrom": {
          "@id": "prov:wasQuotedFrom",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id"
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "wasRevisionOf": {
          "@id": "prov:wasRevisionOf",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id"
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "mentionOf": {
          "@id": "prov:mentionOf",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id"
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "qualifiedGeneration": {
          "@id": "prov:qualifiedGeneration",
          "@type": "@id",
          "@context": {
            "atTime": {
              "@id": "prov:atTime",
              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
            },
            "activity": {
              "@id": "prov:activity",
              "@type": "@id"
            }
          }
        },
        "qualifiedInvalidation": {
          "@id": "prov:qualifiedInvalidation",
          "@type": "@id",
          "@context": {
            "atTime": {
              "@id": "prov:atTime",
              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
            },
            "activity": {
              "@id": "prov:activity",
              "@type": "@id"
            }
          }
        },
        "qualifiedDerivation": {
          "@id": "prov:qualifiedDerivation",
          "@type": "@id",
          "@context": {
            "hadGeneration": {
              "@id": "prov:hadGeneration",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                }
              }
            },
            "hadActivity": {
              "@id": "prov:hadActivity",
              "@type": "@id"
            },
            "hadUsage": {
              "@id": "prov:hadUsage",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                }
              }
            },
            "entity": {
              "@id": "prov:entity",
              "@type": "@id"
            }
          }
        },
        "qualifiedAttribution": {
          "@id": "prov:qualifiedAttribution",
          "@type": "@id",
          "@context": {
            "agent": {
              "@id": "prov:agent",
              "@type": "@id",
              "@context": {
                "wasInfluencedBy": {
                  "@id": "prov:wasInfluencedBy",
                  "@type": "@id",
                  "@context": {}
                },
                "qualifiedInfluence": {
                  "@id": "prov:qualifiedInfluence",
                  "@type": "@id",
                  "@context": {
                    "influencer": {
                      "@id": "prov:influencer",
                      "@type": "@id",
                      "@context": {}
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    },
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id",
                      "@context": {}
                    }
                  }
                }
              }
            }
          }
        },
        "hadMember": {
          "@id": "prov:hadMember",
          "@type": "@id",
          "@context": {
            "hadMember": {
              "@id": "prov:hadMember",
              "@type": "@id"
            }
          }
        }
      }
    },
    "atLocation": {
      "@id": "prov:atLocation",
      "@type": "@id"
    },
    "qualifiedUsage": {
      "@id": "prov:qualifiedUsage",
      "@type": "@id",
      "@context": {
        "atTime": {
          "@id": "prov:atTime",
          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
        },
        "entity": {
          "@id": "prov:entity",
          "@type": "@id",
          "@context": {
            "qualifiedDelegation": {
              "@id": "prov:qualifiedDelegation",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              }
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                }
              }
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id",
                  "@context": {
                    "actedOnBehalfOf": {
                      "@id": "prov:actedOnBehalfOf",
                      "@type": "@id"
                    }
                  }
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id",
                  "@context": {
                    "actedOnBehalfOf": {
                      "@id": "prov:actedOnBehalfOf",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "wasGeneratedBy": {
              "@id": "prov:wasGeneratedBy",
              "@type": "@id"
            },
            "wasAttributedTo": {
              "@id": "prov:wasAttributedTo",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                },
                "wasInfluencedBy": {
                  "@id": "prov:wasInfluencedBy",
                  "@type": "@id"
                },
                "qualifiedInfluence": {
                  "@id": "prov:qualifiedInfluence",
                  "@type": "@id",
                  "@context": {
                    "influencer": {
                      "@id": "prov:influencer",
                      "@type": "@id"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    },
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "wasInvalidatedBy": {
              "@id": "prov:wasInvalidatedBy",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                },
                "wasInfluencedBy": {
                  "@id": "prov:wasInfluencedBy",
                  "@type": "@id"
                },
                "qualifiedInfluence": {
                  "@id": "prov:qualifiedInfluence",
                  "@type": "@id",
                  "@context": {
                    "influencer": {
                      "@id": "prov:influencer",
                      "@type": "@id"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    },
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "wasQuotedFrom": {
              "@id": "prov:wasQuotedFrom",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                },
                "wasInfluencedBy": {
                  "@id": "prov:wasInfluencedBy",
                  "@type": "@id"
                },
                "qualifiedInfluence": {
                  "@id": "prov:qualifiedInfluence",
                  "@type": "@id",
                  "@context": {
                    "influencer": {
                      "@id": "prov:influencer",
                      "@type": "@id"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    },
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "wasRevisionOf": {
              "@id": "prov:wasRevisionOf",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                },
                "wasInfluencedBy": {
                  "@id": "prov:wasInfluencedBy",
                  "@type": "@id"
                },
                "qualifiedInfluence": {
                  "@id": "prov:qualifiedInfluence",
                  "@type": "@id",
                  "@context": {
                    "influencer": {
                      "@id": "prov:influencer",
                      "@type": "@id"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    },
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "mentionOf": {
              "@id": "prov:mentionOf",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                },
                "wasInfluencedBy": {
                  "@id": "prov:wasInfluencedBy",
                  "@type": "@id"
                },
                "qualifiedInfluence": {
                  "@id": "prov:qualifiedInfluence",
                  "@type": "@id",
                  "@context": {
                    "influencer": {
                      "@id": "prov:influencer",
                      "@type": "@id"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    },
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "qualifiedGeneration": {
              "@id": "prov:qualifiedGeneration",
              "@type": "@id",
              "@context": {
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedInvalidation": {
              "@id": "prov:qualifiedInvalidation",
              "@type": "@id",
              "@context": {
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedDerivation": {
              "@id": "prov:qualifiedDerivation",
              "@type": "@id",
              "@context": {
                "hadGeneration": {
                  "@id": "prov:hadGeneration",
                  "@type": "@id",
                  "@context": {
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    }
                  }
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                },
                "hadUsage": {
                  "@id": "prov:hadUsage",
                  "@type": "@id"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedAttribution": {
              "@id": "prov:qualifiedAttribution",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id",
                  "@context": {
                    "wasInfluencedBy": {
                      "@id": "prov:wasInfluencedBy",
                      "@type": "@id",
                      "@context": {}
                    },
                    "qualifiedInfluence": {
                      "@id": "prov:qualifiedInfluence",
                      "@type": "@id",
                      "@context": {
                        "influencer": {
                          "@id": "prov:influencer",
                          "@type": "@id",
                          "@context": {}
                        },
                        "entity": {
                          "@id": "prov:entity",
                          "@type": "@id"
                        },
                        "activity": {
                          "@id": "prov:activity",
                          "@type": "@id"
                        },
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id",
                          "@context": {}
                        }
                      }
                    }
                  }
                }
              }
            },
            "hadMember": {
              "@id": "prov:hadMember",
              "@type": "@id",
              "@context": {
                "hadMember": {
                  "@id": "prov:hadMember",
                  "@type": "@id"
                }
              }
            }
          }
        }
      }
    },
    "qualifiedCommunication": {
      "@id": "prov:qualifiedCommunication",
      "@type": "@id",
      "@context": {
        "activity": {
          "@id": "prov:activity",
          "@type": "@id"
        },
        "atTime": {
          "@id": "prov:atTime",
          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
        }
      }
    },
    "qualifiedStart": {
      "@id": "prov:qualifiedStart",
      "@type": "@id",
      "@context": {
        "atTime": {
          "@id": "prov:atTime",
          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
        },
        "entity": {
          "@id": "prov:entity",
          "@type": "@id",
          "@context": {
            "qualifiedDelegation": {
              "@id": "prov:qualifiedDelegation",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              }
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                }
              }
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id",
                  "@context": {
                    "actedOnBehalfOf": {
                      "@id": "prov:actedOnBehalfOf",
                      "@type": "@id"
                    }
                  }
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id",
                  "@context": {
                    "actedOnBehalfOf": {
                      "@id": "prov:actedOnBehalfOf",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "wasGeneratedBy": {
              "@id": "prov:wasGeneratedBy",
              "@type": "@id"
            },
            "wasAttributedTo": {
              "@id": "prov:wasAttributedTo",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                },
                "wasInfluencedBy": {
                  "@id": "prov:wasInfluencedBy",
                  "@type": "@id"
                },
                "qualifiedInfluence": {
                  "@id": "prov:qualifiedInfluence",
                  "@type": "@id",
                  "@context": {
                    "influencer": {
                      "@id": "prov:influencer",
                      "@type": "@id"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    },
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "wasInvalidatedBy": {
              "@id": "prov:wasInvalidatedBy",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                },
                "wasInfluencedBy": {
                  "@id": "prov:wasInfluencedBy",
                  "@type": "@id"
                },
                "qualifiedInfluence": {
                  "@id": "prov:qualifiedInfluence",
                  "@type": "@id",
                  "@context": {
                    "influencer": {
                      "@id": "prov:influencer",
                      "@type": "@id"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    },
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "wasQuotedFrom": {
              "@id": "prov:wasQuotedFrom",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                },
                "wasInfluencedBy": {
                  "@id": "prov:wasInfluencedBy",
                  "@type": "@id"
                },
                "qualifiedInfluence": {
                  "@id": "prov:qualifiedInfluence",
                  "@type": "@id",
                  "@context": {
                    "influencer": {
                      "@id": "prov:influencer",
                      "@type": "@id"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    },
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "wasRevisionOf": {
              "@id": "prov:wasRevisionOf",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                },
                "wasInfluencedBy": {
                  "@id": "prov:wasInfluencedBy",
                  "@type": "@id"
                },
                "qualifiedInfluence": {
                  "@id": "prov:qualifiedInfluence",
                  "@type": "@id",
                  "@context": {
                    "influencer": {
                      "@id": "prov:influencer",
                      "@type": "@id"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    },
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "mentionOf": {
              "@id": "prov:mentionOf",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                },
                "wasInfluencedBy": {
                  "@id": "prov:wasInfluencedBy",
                  "@type": "@id"
                },
                "qualifiedInfluence": {
                  "@id": "prov:qualifiedInfluence",
                  "@type": "@id",
                  "@context": {
                    "influencer": {
                      "@id": "prov:influencer",
                      "@type": "@id"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    },
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "qualifiedGeneration": {
              "@id": "prov:qualifiedGeneration",
              "@type": "@id",
              "@context": {
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedInvalidation": {
              "@id": "prov:qualifiedInvalidation",
              "@type": "@id",
              "@context": {
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedDerivation": {
              "@id": "prov:qualifiedDerivation",
              "@type": "@id",
              "@context": {
                "hadGeneration": {
                  "@id": "prov:hadGeneration",
                  "@type": "@id",
                  "@context": {
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    }
                  }
                },
                "hadUsage": {
                  "@id": "prov:hadUsage",
                  "@type": "@id",
                  "@context": {}
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedAttribution": {
              "@id": "prov:qualifiedAttribution",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id",
                  "@context": {
                    "wasInfluencedBy": {
                      "@id": "prov:wasInfluencedBy",
                      "@type": "@id",
                      "@context": {}
                    },
                    "qualifiedInfluence": {
                      "@id": "prov:qualifiedInfluence",
                      "@type": "@id",
                      "@context": {
                        "influencer": {
                          "@id": "prov:influencer",
                          "@type": "@id",
                          "@context": {}
                        },
                        "entity": {
                          "@id": "prov:entity",
                          "@type": "@id"
                        },
                        "activity": {
                          "@id": "prov:activity",
                          "@type": "@id"
                        },
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id",
                          "@context": {}
                        }
                      }
                    }
                  }
                }
              }
            },
            "hadMember": {
              "@id": "prov:hadMember",
              "@type": "@id",
              "@context": {
                "hadMember": {
                  "@id": "prov:hadMember",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "hadActivity": {
          "@id": "prov:hadActivity",
          "@type": "@id"
        }
      }
    },
    "qualifiedEnd": {
      "@id": "prov:qualifiedEnd",
      "@type": "@id",
      "@context": {
        "atTime": {
          "@id": "prov:atTime",
          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
        },
        "entity": {
          "@id": "prov:entity",
          "@type": "@id",
          "@context": {
            "qualifiedDelegation": {
              "@id": "prov:qualifiedDelegation",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              }
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                }
              }
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id",
                  "@context": {
                    "actedOnBehalfOf": {
                      "@id": "prov:actedOnBehalfOf",
                      "@type": "@id"
                    }
                  }
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id",
                  "@context": {
                    "actedOnBehalfOf": {
                      "@id": "prov:actedOnBehalfOf",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "wasGeneratedBy": {
              "@id": "prov:wasGeneratedBy",
              "@type": "@id"
            },
            "wasAttributedTo": {
              "@id": "prov:wasAttributedTo",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                },
                "wasInfluencedBy": {
                  "@id": "prov:wasInfluencedBy",
                  "@type": "@id"
                },
                "qualifiedInfluence": {
                  "@id": "prov:qualifiedInfluence",
                  "@type": "@id",
                  "@context": {
                    "influencer": {
                      "@id": "prov:influencer",
                      "@type": "@id"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    },
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "wasInvalidatedBy": {
              "@id": "prov:wasInvalidatedBy",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                },
                "wasInfluencedBy": {
                  "@id": "prov:wasInfluencedBy",
                  "@type": "@id"
                },
                "qualifiedInfluence": {
                  "@id": "prov:qualifiedInfluence",
                  "@type": "@id",
                  "@context": {
                    "influencer": {
                      "@id": "prov:influencer",
                      "@type": "@id"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    },
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "wasQuotedFrom": {
              "@id": "prov:wasQuotedFrom",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                },
                "wasInfluencedBy": {
                  "@id": "prov:wasInfluencedBy",
                  "@type": "@id"
                },
                "qualifiedInfluence": {
                  "@id": "prov:qualifiedInfluence",
                  "@type": "@id",
                  "@context": {
                    "influencer": {
                      "@id": "prov:influencer",
                      "@type": "@id"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    },
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "wasRevisionOf": {
              "@id": "prov:wasRevisionOf",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                },
                "wasInfluencedBy": {
                  "@id": "prov:wasInfluencedBy",
                  "@type": "@id"
                },
                "qualifiedInfluence": {
                  "@id": "prov:qualifiedInfluence",
                  "@type": "@id",
                  "@context": {
                    "influencer": {
                      "@id": "prov:influencer",
                      "@type": "@id"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    },
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "mentionOf": {
              "@id": "prov:mentionOf",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                },
                "wasInfluencedBy": {
                  "@id": "prov:wasInfluencedBy",
                  "@type": "@id"
                },
                "qualifiedInfluence": {
                  "@id": "prov:qualifiedInfluence",
                  "@type": "@id",
                  "@context": {
                    "influencer": {
                      "@id": "prov:influencer",
                      "@type": "@id"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    },
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "qualifiedGeneration": {
              "@id": "prov:qualifiedGeneration",
              "@type": "@id",
              "@context": {
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedInvalidation": {
              "@id": "prov:qualifiedInvalidation",
              "@type": "@id",
              "@context": {
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedDerivation": {
              "@id": "prov:qualifiedDerivation",
              "@type": "@id",
              "@context": {
                "hadGeneration": {
                  "@id": "prov:hadGeneration",
                  "@type": "@id",
                  "@context": {
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    }
                  }
                },
                "hadUsage": {
                  "@id": "prov:hadUsage",
                  "@type": "@id",
                  "@context": {}
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedAttribution": {
              "@id": "prov:qualifiedAttribution",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id",
                  "@context": {
                    "wasInfluencedBy": {
                      "@id": "prov:wasInfluencedBy",
                      "@type": "@id",
                      "@context": {}
                    },
                    "qualifiedInfluence": {
                      "@id": "prov:qualifiedInfluence",
                      "@type": "@id",
                      "@context": {
                        "influencer": {
                          "@id": "prov:influencer",
                          "@type": "@id",
                          "@context": {}
                        },
                        "entity": {
                          "@id": "prov:entity",
                          "@type": "@id"
                        },
                        "activity": {
                          "@id": "prov:activity",
                          "@type": "@id"
                        },
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id",
                          "@context": {}
                        }
                      }
                    }
                  }
                }
              }
            },
            "hadMember": {
              "@id": "prov:hadMember",
              "@type": "@id",
              "@context": {
                "hadMember": {
                  "@id": "prov:hadMember",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "hadActivity": {
          "@id": "prov:hadActivity",
          "@type": "@id"
        }
      }
    },
    "qualifiedAssociation": {
      "@id": "prov:qualifiedAssociation",
      "@type": "@id",
      "@context": {
        "agent": {
          "@id": "prov:agent",
          "@type": "@id",
          "@context": {
            "qualifiedDelegation": {
              "@id": "prov:qualifiedDelegation",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              }
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id",
              "@context": {
                "wasGeneratedBy": {
                  "@id": "prov:wasGeneratedBy",
                  "@type": "@id"
                },
                "wasAttributedTo": {
                  "@id": "prov:wasAttributedTo",
                  "@type": "@id",
                  "@context": {}
                },
                "wasInvalidatedBy": {
                  "@id": "prov:wasInvalidatedBy",
                  "@type": "@id",
                  "@context": {}
                },
                "wasQuotedFrom": {
                  "@id": "prov:wasQuotedFrom",
                  "@type": "@id",
                  "@context": {}
                },
                "wasRevisionOf": {
                  "@id": "prov:wasRevisionOf",
                  "@type": "@id",
                  "@context": {}
                },
                "mentionOf": {
                  "@id": "prov:mentionOf",
                  "@type": "@id",
                  "@context": {}
                },
                "qualifiedGeneration": {
                  "@id": "prov:qualifiedGeneration",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedInvalidation": {
                  "@id": "prov:qualifiedInvalidation",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedDerivation": {
                  "@id": "prov:qualifiedDerivation",
                  "@type": "@id",
                  "@context": {
                    "hadGeneration": {
                      "@id": "prov:hadGeneration",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        },
                        "activity": {
                          "@id": "prov:activity",
                          "@type": "@id"
                        }
                      }
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    },
                    "hadUsage": {
                      "@id": "prov:hadUsage",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        }
                      }
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedAttribution": {
                  "@id": "prov:qualifiedAttribution",
                  "@type": "@id",
                  "@context": {
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    }
                  }
                },
                "hadMember": {
                  "@id": "prov:hadMember",
                  "@type": "@id",
                  "@context": {
                    "hadMember": {
                      "@id": "prov:hadMember",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id",
                  "@context": {
                    "wasGeneratedBy": {
                      "@id": "prov:wasGeneratedBy",
                      "@type": "@id"
                    },
                    "wasAttributedTo": {
                      "@id": "prov:wasAttributedTo",
                      "@type": "@id",
                      "@context": {}
                    },
                    "wasInvalidatedBy": {
                      "@id": "prov:wasInvalidatedBy",
                      "@type": "@id",
                      "@context": {}
                    },
                    "wasQuotedFrom": {
                      "@id": "prov:wasQuotedFrom",
                      "@type": "@id",
                      "@context": {}
                    },
                    "wasRevisionOf": {
                      "@id": "prov:wasRevisionOf",
                      "@type": "@id",
                      "@context": {}
                    },
                    "mentionOf": {
                      "@id": "prov:mentionOf",
                      "@type": "@id",
                      "@context": {}
                    },
                    "qualifiedGeneration": {
                      "@id": "prov:qualifiedGeneration",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        }
                      }
                    },
                    "qualifiedInvalidation": {
                      "@id": "prov:qualifiedInvalidation",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        }
                      }
                    },
                    "qualifiedDerivation": {
                      "@id": "prov:qualifiedDerivation",
                      "@type": "@id",
                      "@context": {
                        "hadGeneration": {
                          "@id": "prov:hadGeneration",
                          "@type": "@id",
                          "@context": {
                            "atTime": {
                              "@id": "prov:atTime",
                              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                            }
                          }
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        },
                        "hadUsage": {
                          "@id": "prov:hadUsage",
                          "@type": "@id",
                          "@context": {
                            "atTime": {
                              "@id": "prov:atTime",
                              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                            }
                          }
                        },
                        "entity": {
                          "@id": "prov:entity",
                          "@type": "@id"
                        }
                      }
                    },
                    "qualifiedAttribution": {
                      "@id": "prov:qualifiedAttribution",
                      "@type": "@id",
                      "@context": {
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id"
                        }
                      }
                    },
                    "hadMember": {
                      "@id": "prov:hadMember",
                      "@type": "@id",
                      "@context": {
                        "hadMember": {
                          "@id": "prov:hadMember",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id",
                  "@context": {
                    "wasGeneratedBy": {
                      "@id": "prov:wasGeneratedBy",
                      "@type": "@id"
                    },
                    "wasAttributedTo": {
                      "@id": "prov:wasAttributedTo",
                      "@type": "@id",
                      "@context": {}
                    },
                    "wasInvalidatedBy": {
                      "@id": "prov:wasInvalidatedBy",
                      "@type": "@id",
                      "@context": {}
                    },
                    "wasQuotedFrom": {
                      "@id": "prov:wasQuotedFrom",
                      "@type": "@id",
                      "@context": {}
                    },
                    "wasRevisionOf": {
                      "@id": "prov:wasRevisionOf",
                      "@type": "@id",
                      "@context": {}
                    },
                    "mentionOf": {
                      "@id": "prov:mentionOf",
                      "@type": "@id",
                      "@context": {}
                    },
                    "qualifiedGeneration": {
                      "@id": "prov:qualifiedGeneration",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        }
                      }
                    },
                    "qualifiedInvalidation": {
                      "@id": "prov:qualifiedInvalidation",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        }
                      }
                    },
                    "qualifiedDerivation": {
                      "@id": "prov:qualifiedDerivation",
                      "@type": "@id",
                      "@context": {
                        "hadGeneration": {
                          "@id": "prov:hadGeneration",
                          "@type": "@id",
                          "@context": {
                            "atTime": {
                              "@id": "prov:atTime",
                              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                            }
                          }
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        },
                        "hadUsage": {
                          "@id": "prov:hadUsage",
                          "@type": "@id",
                          "@context": {
                            "atTime": {
                              "@id": "prov:atTime",
                              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                            }
                          }
                        },
                        "entity": {
                          "@id": "prov:entity",
                          "@type": "@id"
                        }
                      }
                    },
                    "qualifiedAttribution": {
                      "@id": "prov:qualifiedAttribution",
                      "@type": "@id",
                      "@context": {
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id"
                        }
                      }
                    },
                    "hadMember": {
                      "@id": "prov:hadMember",
                      "@type": "@id",
                      "@context": {
                        "hadMember": {
                          "@id": "prov:hadMember",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id",
                  "@context": {}
                }
              }
            }
          }
        },
        "hadRole": {
          "@id": "prov:hadRole",
          "@type": "@id"
        },
        "hadPlan": {
          "@id": "prov:hadPlan",
          "@type": "@id"
        }
      }
    },
    "wasInfluencedBy": {
      "@id": "prov:wasInfluencedBy",
      "@type": "@id",
      "@context": {
        "qualifiedDelegation": {
          "@id": "prov:qualifiedDelegation",
          "@type": "@id",
          "@context": {
            "agent": {
              "@id": "prov:agent",
              "@type": "@id"
            },
            "hadActivity": {
              "@id": "prov:hadActivity",
              "@type": "@id",
              "@context": {
                "wasAssociatedWith": {
                  "@id": "prov:wasAssociatedWith",
                  "@type": "@id"
                },
                "qualifiedAssociation": {
                  "@id": "prov:qualifiedAssociation",
                  "@type": "@id",
                  "@context": {
                    "hadRole": {
                      "@id": "prov:hadRole",
                      "@type": "@id"
                    },
                    "hadPlan": {
                      "@id": "prov:hadPlan",
                      "@type": "@id"
                    }
                  }
                }
              }
            }
          }
        },
        "wasAssociatedWith": {
          "@id": "prov:wasAssociatedWith",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "qualifiedDelegation": {
              "@id": "prov:qualifiedDelegation",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "used": {
          "@id": "prov:used",
          "@type": "@id"
        },
        "wasStartedBy": {
          "@id": "prov:wasStartedBy",
          "@type": "@id"
        },
        "wasEndedBy": {
          "@id": "prov:wasEndedBy",
          "@type": "@id"
        },
        "invalidated": {
          "@id": "prov:invalidated",
          "@type": "@id"
        },
        "generated": {
          "@id": "prov:generated",
          "@type": "@id"
        },
        "qualifiedUsage": {
          "@id": "prov:qualifiedUsage",
          "@type": "@id",
          "@context": {
            "atTime": {
              "@id": "prov:atTime",
              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
            },
            "entity": {
              "@id": "prov:entity",
              "@type": "@id"
            }
          }
        },
        "qualifiedStart": {
          "@id": "prov:qualifiedStart",
          "@type": "@id",
          "@context": {
            "atTime": {
              "@id": "prov:atTime",
              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
            },
            "entity": {
              "@id": "prov:entity",
              "@type": "@id"
            },
            "hadActivity": {
              "@id": "prov:hadActivity",
              "@type": "@id"
            }
          }
        },
        "qualifiedEnd": {
          "@id": "prov:qualifiedEnd",
          "@type": "@id",
          "@context": {
            "atTime": {
              "@id": "prov:atTime",
              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
            },
            "entity": {
              "@id": "prov:entity",
              "@type": "@id"
            },
            "hadActivity": {
              "@id": "prov:hadActivity",
              "@type": "@id"
            }
          }
        },
        "qualifiedAssociation": {
          "@id": "prov:qualifiedAssociation",
          "@type": "@id",
          "@context": {
            "agent": {
              "@id": "prov:agent",
              "@type": "@id",
              "@context": {
                "qualifiedDelegation": {
                  "@id": "prov:qualifiedDelegation",
                  "@type": "@id",
                  "@context": {
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "hadRole": {
              "@id": "prov:hadRole",
              "@type": "@id"
            },
            "hadPlan": {
              "@id": "prov:hadPlan",
              "@type": "@id"
            }
          }
        },
        "wasGeneratedBy": {
          "@id": "prov:wasGeneratedBy",
          "@type": "@id"
        },
        "wasAttributedTo": {
          "@id": "prov:wasAttributedTo",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "qualifiedDelegation": {
              "@id": "prov:qualifiedDelegation",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "wasInvalidatedBy": {
          "@id": "prov:wasInvalidatedBy",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "qualifiedDelegation": {
              "@id": "prov:qualifiedDelegation",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "wasQuotedFrom": {
          "@id": "prov:wasQuotedFrom",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "qualifiedDelegation": {
              "@id": "prov:qualifiedDelegation",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "wasRevisionOf": {
          "@id": "prov:wasRevisionOf",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "qualifiedDelegation": {
              "@id": "prov:qualifiedDelegation",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "mentionOf": {
          "@id": "prov:mentionOf",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "qualifiedDelegation": {
              "@id": "prov:qualifiedDelegation",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "qualifiedGeneration": {
          "@id": "prov:qualifiedGeneration",
          "@type": "@id",
          "@context": {
            "atTime": {
              "@id": "prov:atTime",
              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
            },
            "activity": {
              "@id": "prov:activity",
              "@type": "@id"
            }
          }
        },
        "qualifiedInvalidation": {
          "@id": "prov:qualifiedInvalidation",
          "@type": "@id",
          "@context": {
            "atTime": {
              "@id": "prov:atTime",
              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
            },
            "activity": {
              "@id": "prov:activity",
              "@type": "@id"
            }
          }
        },
        "qualifiedDerivation": {
          "@id": "prov:qualifiedDerivation",
          "@type": "@id",
          "@context": {
            "hadGeneration": {
              "@id": "prov:hadGeneration",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                }
              }
            },
            "hadActivity": {
              "@id": "prov:hadActivity",
              "@type": "@id"
            },
            "hadUsage": {
              "@id": "prov:hadUsage",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                }
              }
            },
            "entity": {
              "@id": "prov:entity",
              "@type": "@id"
            }
          }
        },
        "qualifiedAttribution": {
          "@id": "prov:qualifiedAttribution",
          "@type": "@id",
          "@context": {
            "agent": {
              "@id": "prov:agent",
              "@type": "@id",
              "@context": {
                "qualifiedDelegation": {
                  "@id": "prov:qualifiedDelegation",
                  "@type": "@id",
                  "@context": {
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                }
              }
            }
          }
        },
        "hadMember": {
          "@id": "prov:hadMember",
          "@type": "@id",
          "@context": {
            "qualifiedDelegation": {
              "@id": "prov:qualifiedDelegation",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              }
            },
            "wasAttributedTo": {
              "@id": "prov:wasAttributedTo",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                }
              }
            },
            "wasInvalidatedBy": {
              "@id": "prov:wasInvalidatedBy",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                }
              }
            },
            "wasQuotedFrom": {
              "@id": "prov:wasQuotedFrom",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                }
              }
            },
            "wasRevisionOf": {
              "@id": "prov:wasRevisionOf",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                }
              }
            },
            "mentionOf": {
              "@id": "prov:mentionOf",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                }
              }
            },
            "qualifiedAttribution": {
              "@id": "prov:qualifiedAttribution",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id",
                  "@context": {}
                }
              }
            },
            "hadMember": {
              "@id": "prov:hadMember",
              "@type": "@id"
            }
          }
        }
      }
    },
    "qualifiedInfluence": {
      "@id": "prov:qualifiedInfluence",
      "@type": "@id",
      "@context": {
        "influencer": {
          "@id": "prov:influencer",
          "@type": "@id",
          "@context": {
            "qualifiedDelegation": {
              "@id": "prov:qualifiedDelegation",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id",
                  "@context": {
                    "wasAssociatedWith": {
                      "@id": "prov:wasAssociatedWith",
                      "@type": "@id"
                    },
                    "qualifiedAssociation": {
                      "@id": "prov:qualifiedAssociation",
                      "@type": "@id",
                      "@context": {
                        "hadRole": {
                          "@id": "prov:hadRole",
                          "@type": "@id"
                        },
                        "hadPlan": {
                          "@id": "prov:hadPlan",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                }
              }
            },
            "wasAssociatedWith": {
              "@id": "prov:wasAssociatedWith",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                },
                "qualifiedDelegation": {
                  "@id": "prov:qualifiedDelegation",
                  "@type": "@id",
                  "@context": {
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "used": {
              "@id": "prov:used",
              "@type": "@id"
            },
            "wasStartedBy": {
              "@id": "prov:wasStartedBy",
              "@type": "@id"
            },
            "wasEndedBy": {
              "@id": "prov:wasEndedBy",
              "@type": "@id"
            },
            "invalidated": {
              "@id": "prov:invalidated",
              "@type": "@id"
            },
            "generated": {
              "@id": "prov:generated",
              "@type": "@id"
            },
            "qualifiedUsage": {
              "@id": "prov:qualifiedUsage",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedStart": {
              "@id": "prov:qualifiedStart",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedEnd": {
              "@id": "prov:qualifiedEnd",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedAssociation": {
              "@id": "prov:qualifiedAssociation",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id",
                  "@context": {
                    "qualifiedDelegation": {
                      "@id": "prov:qualifiedDelegation",
                      "@type": "@id",
                      "@context": {
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                },
                "hadRole": {
                  "@id": "prov:hadRole",
                  "@type": "@id"
                },
                "hadPlan": {
                  "@id": "prov:hadPlan",
                  "@type": "@id"
                }
              }
            },
            "wasGeneratedBy": {
              "@id": "prov:wasGeneratedBy",
              "@type": "@id"
            },
            "wasAttributedTo": {
              "@id": "prov:wasAttributedTo",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                },
                "qualifiedDelegation": {
                  "@id": "prov:qualifiedDelegation",
                  "@type": "@id",
                  "@context": {
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "wasInvalidatedBy": {
              "@id": "prov:wasInvalidatedBy",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                },
                "qualifiedDelegation": {
                  "@id": "prov:qualifiedDelegation",
                  "@type": "@id",
                  "@context": {
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "wasQuotedFrom": {
              "@id": "prov:wasQuotedFrom",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                },
                "qualifiedDelegation": {
                  "@id": "prov:qualifiedDelegation",
                  "@type": "@id",
                  "@context": {
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "wasRevisionOf": {
              "@id": "prov:wasRevisionOf",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                },
                "qualifiedDelegation": {
                  "@id": "prov:qualifiedDelegation",
                  "@type": "@id",
                  "@context": {
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "mentionOf": {
              "@id": "prov:mentionOf",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                },
                "qualifiedDelegation": {
                  "@id": "prov:qualifiedDelegation",
                  "@type": "@id",
                  "@context": {
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "qualifiedGeneration": {
              "@id": "prov:qualifiedGeneration",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedInvalidation": {
              "@id": "prov:qualifiedInvalidation",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedDerivation": {
              "@id": "prov:qualifiedDerivation",
              "@type": "@id",
              "@context": {
                "hadGeneration": {
                  "@id": "prov:hadGeneration",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    }
                  }
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                },
                "hadUsage": {
                  "@id": "prov:hadUsage",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    }
                  }
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedAttribution": {
              "@id": "prov:qualifiedAttribution",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id",
                  "@context": {
                    "qualifiedDelegation": {
                      "@id": "prov:qualifiedDelegation",
                      "@type": "@id",
                      "@context": {
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                }
              }
            },
            "hadMember": {
              "@id": "prov:hadMember",
              "@type": "@id",
              "@context": {
                "qualifiedDelegation": {
                  "@id": "prov:qualifiedDelegation",
                  "@type": "@id",
                  "@context": {
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "wasAttributedTo": {
                  "@id": "prov:wasAttributedTo",
                  "@type": "@id",
                  "@context": {
                    "actedOnBehalfOf": {
                      "@id": "prov:actedOnBehalfOf",
                      "@type": "@id"
                    }
                  }
                },
                "wasInvalidatedBy": {
                  "@id": "prov:wasInvalidatedBy",
                  "@type": "@id",
                  "@context": {
                    "actedOnBehalfOf": {
                      "@id": "prov:actedOnBehalfOf",
                      "@type": "@id"
                    }
                  }
                },
                "wasQuotedFrom": {
                  "@id": "prov:wasQuotedFrom",
                  "@type": "@id",
                  "@context": {
                    "actedOnBehalfOf": {
                      "@id": "prov:actedOnBehalfOf",
                      "@type": "@id"
                    }
                  }
                },
                "wasRevisionOf": {
                  "@id": "prov:wasRevisionOf",
                  "@type": "@id",
                  "@context": {
                    "actedOnBehalfOf": {
                      "@id": "prov:actedOnBehalfOf",
                      "@type": "@id"
                    }
                  }
                },
                "mentionOf": {
                  "@id": "prov:mentionOf",
                  "@type": "@id",
                  "@context": {
                    "actedOnBehalfOf": {
                      "@id": "prov:actedOnBehalfOf",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedAttribution": {
                  "@id": "prov:qualifiedAttribution",
                  "@type": "@id",
                  "@context": {
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id",
                      "@context": {}
                    }
                  }
                },
                "hadMember": {
                  "@id": "prov:hadMember",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "entity": {
          "@id": "prov:entity",
          "@type": "@id",
          "@context": {
            "qualifiedDelegation": {
              "@id": "prov:qualifiedDelegation",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              }
            },
            "wasGeneratedBy": {
              "@id": "prov:wasGeneratedBy",
              "@type": "@id"
            },
            "wasAttributedTo": {
              "@id": "prov:wasAttributedTo",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                }
              }
            },
            "wasInvalidatedBy": {
              "@id": "prov:wasInvalidatedBy",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                }
              }
            },
            "wasQuotedFrom": {
              "@id": "prov:wasQuotedFrom",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                }
              }
            },
            "wasRevisionOf": {
              "@id": "prov:wasRevisionOf",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                }
              }
            },
            "mentionOf": {
              "@id": "prov:mentionOf",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                }
              }
            },
            "qualifiedGeneration": {
              "@id": "prov:qualifiedGeneration",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedInvalidation": {
              "@id": "prov:qualifiedInvalidation",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedDerivation": {
              "@id": "prov:qualifiedDerivation",
              "@type": "@id",
              "@context": {
                "hadGeneration": {
                  "@id": "prov:hadGeneration",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    }
                  }
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                },
                "hadUsage": {
                  "@id": "prov:hadUsage",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    }
                  }
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedAttribution": {
              "@id": "prov:qualifiedAttribution",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id",
                  "@context": {}
                }
              }
            },
            "hadMember": {
              "@id": "prov:hadMember",
              "@type": "@id",
              "@context": {
                "hadMember": {
                  "@id": "prov:hadMember",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "activity": {
          "@id": "prov:activity",
          "@type": "@id",
          "@context": {
            "wasAssociatedWith": {
              "@id": "prov:wasAssociatedWith",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                },
                "qualifiedDelegation": {
                  "@id": "prov:qualifiedDelegation",
                  "@type": "@id",
                  "@context": {
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "used": {
              "@id": "prov:used",
              "@type": "@id"
            },
            "wasStartedBy": {
              "@id": "prov:wasStartedBy",
              "@type": "@id"
            },
            "wasEndedBy": {
              "@id": "prov:wasEndedBy",
              "@type": "@id"
            },
            "invalidated": {
              "@id": "prov:invalidated",
              "@type": "@id"
            },
            "generated": {
              "@id": "prov:generated",
              "@type": "@id"
            },
            "qualifiedUsage": {
              "@id": "prov:qualifiedUsage",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedStart": {
              "@id": "prov:qualifiedStart",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedEnd": {
              "@id": "prov:qualifiedEnd",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedAssociation": {
              "@id": "prov:qualifiedAssociation",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id",
                  "@context": {
                    "qualifiedDelegation": {
                      "@id": "prov:qualifiedDelegation",
                      "@type": "@id",
                      "@context": {
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                },
                "hadRole": {
                  "@id": "prov:hadRole",
                  "@type": "@id"
                },
                "hadPlan": {
                  "@id": "prov:hadPlan",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "agent": {
          "@id": "prov:agent",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "qualifiedDelegation": {
              "@id": "prov:qualifiedDelegation",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id",
                  "@context": {
                    "wasAssociatedWith": {
                      "@id": "prov:wasAssociatedWith",
                      "@type": "@id"
                    },
                    "used": {
                      "@id": "prov:used",
                      "@type": "@id"
                    },
                    "wasStartedBy": {
                      "@id": "prov:wasStartedBy",
                      "@type": "@id"
                    },
                    "wasEndedBy": {
                      "@id": "prov:wasEndedBy",
                      "@type": "@id"
                    },
                    "invalidated": {
                      "@id": "prov:invalidated",
                      "@type": "@id"
                    },
                    "generated": {
                      "@id": "prov:generated",
                      "@type": "@id"
                    },
                    "qualifiedUsage": {
                      "@id": "prov:qualifiedUsage",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        },
                        "entity": {
                          "@id": "prov:entity",
                          "@type": "@id"
                        }
                      }
                    },
                    "qualifiedStart": {
                      "@id": "prov:qualifiedStart",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        },
                        "entity": {
                          "@id": "prov:entity",
                          "@type": "@id"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    },
                    "qualifiedEnd": {
                      "@id": "prov:qualifiedEnd",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        },
                        "entity": {
                          "@id": "prov:entity",
                          "@type": "@id"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    },
                    "qualifiedAssociation": {
                      "@id": "prov:qualifiedAssociation",
                      "@type": "@id",
                      "@context": {
                        "hadRole": {
                          "@id": "prov:hadRole",
                          "@type": "@id"
                        },
                        "hadPlan": {
                          "@id": "prov:hadPlan",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                }
              }
            }
          }
        }
      }
    },
    "name": "rdfs:label",
    "actedOnBehalfOf": {
      "@id": "prov:actedOnBehalfOf",
      "@type": "@id",
      "@context": {}
    },
    "qualifiedDelegation": {
      "@id": "prov:qualifiedDelegation",
      "@type": "@id",
      "@context": {
        "agent": {
          "@id": "prov:agent",
          "@type": "@id"
        },
        "hadActivity": {
          "@id": "prov:hadActivity",
          "@type": "@id",
          "@context": {
            "wasAssociatedWith": {
              "@id": "prov:wasAssociatedWith",
              "@type": "@id",
              "@context": {}
            },
            "used": {
              "@id": "prov:used",
              "@type": "@id"
            },
            "wasStartedBy": {
              "@id": "prov:wasStartedBy",
              "@type": "@id"
            },
            "wasEndedBy": {
              "@id": "prov:wasEndedBy",
              "@type": "@id"
            },
            "invalidated": {
              "@id": "prov:invalidated",
              "@type": "@id"
            },
            "generated": {
              "@id": "prov:generated",
              "@type": "@id"
            },
            "qualifiedUsage": {
              "@id": "prov:qualifiedUsage",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedStart": {
              "@id": "prov:qualifiedStart",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedEnd": {
              "@id": "prov:qualifiedEnd",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedAssociation": {
              "@id": "prov:qualifiedAssociation",
              "@type": "@id",
              "@context": {
                "hadRole": {
                  "@id": "prov:hadRole",
                  "@type": "@id"
                },
                "hadPlan": {
                  "@id": "prov:hadPlan",
                  "@type": "@id"
                }
              }
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id",
              "@context": {}
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id",
                  "@context": {}
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id",
                  "@context": {}
                }
              }
            }
          }
        }
      }
    },
    "wasGeneratedBy": {
      "@id": "prov:wasGeneratedBy",
      "@type": "@id",
      "@context": {
        "wasAssociatedWith": {
          "@id": "prov:wasAssociatedWith",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "qualifiedDelegation": {
              "@id": "prov:qualifiedDelegation",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              }
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id"
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "used": {
          "@id": "prov:used",
          "@type": "@id"
        },
        "wasStartedBy": {
          "@id": "prov:wasStartedBy",
          "@type": "@id"
        },
        "wasEndedBy": {
          "@id": "prov:wasEndedBy",
          "@type": "@id"
        },
        "invalidated": {
          "@id": "prov:invalidated",
          "@type": "@id"
        },
        "generated": {
          "@id": "prov:generated",
          "@type": "@id"
        },
        "qualifiedUsage": {
          "@id": "prov:qualifiedUsage",
          "@type": "@id",
          "@context": {
            "atTime": {
              "@id": "prov:atTime",
              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
            },
            "entity": {
              "@id": "prov:entity",
              "@type": "@id"
            }
          }
        },
        "qualifiedStart": {
          "@id": "prov:qualifiedStart",
          "@type": "@id",
          "@context": {
            "atTime": {
              "@id": "prov:atTime",
              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
            },
            "entity": {
              "@id": "prov:entity",
              "@type": "@id"
            },
            "hadActivity": {
              "@id": "prov:hadActivity",
              "@type": "@id"
            }
          }
        },
        "qualifiedEnd": {
          "@id": "prov:qualifiedEnd",
          "@type": "@id",
          "@context": {
            "atTime": {
              "@id": "prov:atTime",
              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
            },
            "entity": {
              "@id": "prov:entity",
              "@type": "@id"
            },
            "hadActivity": {
              "@id": "prov:hadActivity",
              "@type": "@id"
            }
          }
        },
        "qualifiedAssociation": {
          "@id": "prov:qualifiedAssociation",
          "@type": "@id",
          "@context": {
            "agent": {
              "@id": "prov:agent",
              "@type": "@id",
              "@context": {
                "qualifiedDelegation": {
                  "@id": "prov:qualifiedDelegation",
                  "@type": "@id",
                  "@context": {
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "wasInfluencedBy": {
                  "@id": "prov:wasInfluencedBy",
                  "@type": "@id",
                  "@context": {}
                },
                "qualifiedInfluence": {
                  "@id": "prov:qualifiedInfluence",
                  "@type": "@id",
                  "@context": {
                    "influencer": {
                      "@id": "prov:influencer",
                      "@type": "@id",
                      "@context": {}
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    },
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id",
                      "@context": {}
                    }
                  }
                }
              }
            },
            "hadRole": {
              "@id": "prov:hadRole",
              "@type": "@id"
            },
            "hadPlan": {
              "@id": "prov:hadPlan",
              "@type": "@id"
            }
          }
        },
        "wasInfluencedBy": {
          "@id": "prov:wasInfluencedBy",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "qualifiedDelegation": {
              "@id": "prov:qualifiedDelegation",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "qualifiedInfluence": {
          "@id": "prov:qualifiedInfluence",
          "@type": "@id",
          "@context": {
            "influencer": {
              "@id": "prov:influencer",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                },
                "qualifiedDelegation": {
                  "@id": "prov:qualifiedDelegation",
                  "@type": "@id",
                  "@context": {
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "entity": {
              "@id": "prov:entity",
              "@type": "@id"
            },
            "activity": {
              "@id": "prov:activity",
              "@type": "@id"
            },
            "agent": {
              "@id": "prov:agent",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                },
                "qualifiedDelegation": {
                  "@id": "prov:qualifiedDelegation",
                  "@type": "@id",
                  "@context": {
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                }
              }
            }
          }
        }
      }
    },
    "wasAttributedTo": {
      "@id": "prov:wasAttributedTo",
      "@type": "@id",
      "@context": {
        "actedOnBehalfOf": {
          "@id": "prov:actedOnBehalfOf",
          "@type": "@id"
        },
        "qualifiedDelegation": {
          "@id": "prov:qualifiedDelegation",
          "@type": "@id",
          "@context": {
            "agent": {
              "@id": "prov:agent",
              "@type": "@id"
            },
            "hadActivity": {
              "@id": "prov:hadActivity",
              "@type": "@id",
              "@context": {
                "wasAssociatedWith": {
                  "@id": "prov:wasAssociatedWith",
                  "@type": "@id"
                },
                "used": {
                  "@id": "prov:used",
                  "@type": "@id"
                },
                "wasStartedBy": {
                  "@id": "prov:wasStartedBy",
                  "@type": "@id"
                },
                "wasEndedBy": {
                  "@id": "prov:wasEndedBy",
                  "@type": "@id"
                },
                "invalidated": {
                  "@id": "prov:invalidated",
                  "@type": "@id"
                },
                "generated": {
                  "@id": "prov:generated",
                  "@type": "@id"
                },
                "qualifiedUsage": {
                  "@id": "prov:qualifiedUsage",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedStart": {
                  "@id": "prov:qualifiedStart",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedEnd": {
                  "@id": "prov:qualifiedEnd",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedAssociation": {
                  "@id": "prov:qualifiedAssociation",
                  "@type": "@id",
                  "@context": {
                    "hadRole": {
                      "@id": "prov:hadRole",
                      "@type": "@id"
                    },
                    "hadPlan": {
                      "@id": "prov:hadPlan",
                      "@type": "@id"
                    }
                  }
                },
                "wasInfluencedBy": {
                  "@id": "prov:wasInfluencedBy",
                  "@type": "@id"
                },
                "qualifiedInfluence": {
                  "@id": "prov:qualifiedInfluence",
                  "@type": "@id",
                  "@context": {
                    "influencer": {
                      "@id": "prov:influencer",
                      "@type": "@id"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    }
                  }
                }
              }
            }
          }
        },
        "wasInfluencedBy": {
          "@id": "prov:wasInfluencedBy",
          "@type": "@id",
          "@context": {
            "wasAssociatedWith": {
              "@id": "prov:wasAssociatedWith",
              "@type": "@id"
            },
            "used": {
              "@id": "prov:used",
              "@type": "@id"
            },
            "wasStartedBy": {
              "@id": "prov:wasStartedBy",
              "@type": "@id"
            },
            "wasEndedBy": {
              "@id": "prov:wasEndedBy",
              "@type": "@id"
            },
            "invalidated": {
              "@id": "prov:invalidated",
              "@type": "@id"
            },
            "generated": {
              "@id": "prov:generated",
              "@type": "@id"
            },
            "qualifiedUsage": {
              "@id": "prov:qualifiedUsage",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedStart": {
              "@id": "prov:qualifiedStart",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedEnd": {
              "@id": "prov:qualifiedEnd",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedAssociation": {
              "@id": "prov:qualifiedAssociation",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                },
                "hadRole": {
                  "@id": "prov:hadRole",
                  "@type": "@id"
                },
                "hadPlan": {
                  "@id": "prov:hadPlan",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "qualifiedInfluence": {
          "@id": "prov:qualifiedInfluence",
          "@type": "@id",
          "@context": {
            "influencer": {
              "@id": "prov:influencer",
              "@type": "@id",
              "@context": {
                "wasAssociatedWith": {
                  "@id": "prov:wasAssociatedWith",
                  "@type": "@id"
                },
                "used": {
                  "@id": "prov:used",
                  "@type": "@id"
                },
                "wasStartedBy": {
                  "@id": "prov:wasStartedBy",
                  "@type": "@id"
                },
                "wasEndedBy": {
                  "@id": "prov:wasEndedBy",
                  "@type": "@id"
                },
                "invalidated": {
                  "@id": "prov:invalidated",
                  "@type": "@id"
                },
                "generated": {
                  "@id": "prov:generated",
                  "@type": "@id"
                },
                "qualifiedUsage": {
                  "@id": "prov:qualifiedUsage",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    }
                  }
                },
                "qualifiedStart": {
                  "@id": "prov:qualifiedStart",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedEnd": {
                  "@id": "prov:qualifiedEnd",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedAssociation": {
                  "@id": "prov:qualifiedAssociation",
                  "@type": "@id",
                  "@context": {
                    "hadRole": {
                      "@id": "prov:hadRole",
                      "@type": "@id"
                    },
                    "hadPlan": {
                      "@id": "prov:hadPlan",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "entity": {
              "@id": "prov:entity",
              "@type": "@id"
            },
            "activity": {
              "@id": "prov:activity",
              "@type": "@id",
              "@context": {
                "wasAssociatedWith": {
                  "@id": "prov:wasAssociatedWith",
                  "@type": "@id"
                },
                "used": {
                  "@id": "prov:used",
                  "@type": "@id"
                },
                "wasStartedBy": {
                  "@id": "prov:wasStartedBy",
                  "@type": "@id"
                },
                "wasEndedBy": {
                  "@id": "prov:wasEndedBy",
                  "@type": "@id"
                },
                "invalidated": {
                  "@id": "prov:invalidated",
                  "@type": "@id"
                },
                "generated": {
                  "@id": "prov:generated",
                  "@type": "@id"
                },
                "qualifiedUsage": {
                  "@id": "prov:qualifiedUsage",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    }
                  }
                },
                "qualifiedStart": {
                  "@id": "prov:qualifiedStart",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedEnd": {
                  "@id": "prov:qualifiedEnd",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedAssociation": {
                  "@id": "prov:qualifiedAssociation",
                  "@type": "@id",
                  "@context": {
                    "hadRole": {
                      "@id": "prov:hadRole",
                      "@type": "@id"
                    },
                    "hadPlan": {
                      "@id": "prov:hadPlan",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "agent": {
              "@id": "prov:agent",
              "@type": "@id"
            }
          }
        }
      }
    },
    "wasDerivedFrom": {
      "@id": "prov:wasDerivedFrom",
      "@type": "@id"
    },
    "alternateOf": {
      "@id": "prov:alternateOf",
      "@type": "@id"
    },
    "hadPrimarySource": {
      "@id": "prov:hadPrimarySource",
      "@type": "@id"
    },
    "specializationOf": {
      "@id": "prov:specializationOf",
      "@type": "@id"
    },
    "wasInvalidatedBy": {
      "@id": "prov:wasInvalidatedBy",
      "@type": "@id",
      "@context": {
        "actedOnBehalfOf": {
          "@id": "prov:actedOnBehalfOf",
          "@type": "@id"
        },
        "qualifiedDelegation": {
          "@id": "prov:qualifiedDelegation",
          "@type": "@id",
          "@context": {
            "agent": {
              "@id": "prov:agent",
              "@type": "@id"
            },
            "hadActivity": {
              "@id": "prov:hadActivity",
              "@type": "@id",
              "@context": {
                "wasAssociatedWith": {
                  "@id": "prov:wasAssociatedWith",
                  "@type": "@id"
                },
                "used": {
                  "@id": "prov:used",
                  "@type": "@id"
                },
                "wasStartedBy": {
                  "@id": "prov:wasStartedBy",
                  "@type": "@id"
                },
                "wasEndedBy": {
                  "@id": "prov:wasEndedBy",
                  "@type": "@id"
                },
                "invalidated": {
                  "@id": "prov:invalidated",
                  "@type": "@id"
                },
                "generated": {
                  "@id": "prov:generated",
                  "@type": "@id"
                },
                "qualifiedUsage": {
                  "@id": "prov:qualifiedUsage",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedStart": {
                  "@id": "prov:qualifiedStart",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedEnd": {
                  "@id": "prov:qualifiedEnd",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedAssociation": {
                  "@id": "prov:qualifiedAssociation",
                  "@type": "@id",
                  "@context": {
                    "hadRole": {
                      "@id": "prov:hadRole",
                      "@type": "@id"
                    },
                    "hadPlan": {
                      "@id": "prov:hadPlan",
                      "@type": "@id"
                    }
                  }
                },
                "wasInfluencedBy": {
                  "@id": "prov:wasInfluencedBy",
                  "@type": "@id"
                },
                "qualifiedInfluence": {
                  "@id": "prov:qualifiedInfluence",
                  "@type": "@id",
                  "@context": {
                    "influencer": {
                      "@id": "prov:influencer",
                      "@type": "@id"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    }
                  }
                }
              }
            }
          }
        },
        "wasInfluencedBy": {
          "@id": "prov:wasInfluencedBy",
          "@type": "@id",
          "@context": {
            "wasAssociatedWith": {
              "@id": "prov:wasAssociatedWith",
              "@type": "@id"
            },
            "used": {
              "@id": "prov:used",
              "@type": "@id"
            },
            "wasStartedBy": {
              "@id": "prov:wasStartedBy",
              "@type": "@id"
            },
            "wasEndedBy": {
              "@id": "prov:wasEndedBy",
              "@type": "@id"
            },
            "invalidated": {
              "@id": "prov:invalidated",
              "@type": "@id"
            },
            "generated": {
              "@id": "prov:generated",
              "@type": "@id"
            },
            "qualifiedUsage": {
              "@id": "prov:qualifiedUsage",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedStart": {
              "@id": "prov:qualifiedStart",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedEnd": {
              "@id": "prov:qualifiedEnd",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedAssociation": {
              "@id": "prov:qualifiedAssociation",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                },
                "hadRole": {
                  "@id": "prov:hadRole",
                  "@type": "@id"
                },
                "hadPlan": {
                  "@id": "prov:hadPlan",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "qualifiedInfluence": {
          "@id": "prov:qualifiedInfluence",
          "@type": "@id",
          "@context": {
            "influencer": {
              "@id": "prov:influencer",
              "@type": "@id",
              "@context": {
                "wasAssociatedWith": {
                  "@id": "prov:wasAssociatedWith",
                  "@type": "@id"
                },
                "used": {
                  "@id": "prov:used",
                  "@type": "@id"
                },
                "wasStartedBy": {
                  "@id": "prov:wasStartedBy",
                  "@type": "@id"
                },
                "wasEndedBy": {
                  "@id": "prov:wasEndedBy",
                  "@type": "@id"
                },
                "invalidated": {
                  "@id": "prov:invalidated",
                  "@type": "@id"
                },
                "generated": {
                  "@id": "prov:generated",
                  "@type": "@id"
                },
                "qualifiedUsage": {
                  "@id": "prov:qualifiedUsage",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    }
                  }
                },
                "qualifiedStart": {
                  "@id": "prov:qualifiedStart",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedEnd": {
                  "@id": "prov:qualifiedEnd",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedAssociation": {
                  "@id": "prov:qualifiedAssociation",
                  "@type": "@id",
                  "@context": {
                    "hadRole": {
                      "@id": "prov:hadRole",
                      "@type": "@id"
                    },
                    "hadPlan": {
                      "@id": "prov:hadPlan",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "entity": {
              "@id": "prov:entity",
              "@type": "@id"
            },
            "activity": {
              "@id": "prov:activity",
              "@type": "@id",
              "@context": {
                "wasAssociatedWith": {
                  "@id": "prov:wasAssociatedWith",
                  "@type": "@id"
                },
                "used": {
                  "@id": "prov:used",
                  "@type": "@id"
                },
                "wasStartedBy": {
                  "@id": "prov:wasStartedBy",
                  "@type": "@id"
                },
                "wasEndedBy": {
                  "@id": "prov:wasEndedBy",
                  "@type": "@id"
                },
                "invalidated": {
                  "@id": "prov:invalidated",
                  "@type": "@id"
                },
                "generated": {
                  "@id": "prov:generated",
                  "@type": "@id"
                },
                "qualifiedUsage": {
                  "@id": "prov:qualifiedUsage",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    }
                  }
                },
                "qualifiedStart": {
                  "@id": "prov:qualifiedStart",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedEnd": {
                  "@id": "prov:qualifiedEnd",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedAssociation": {
                  "@id": "prov:qualifiedAssociation",
                  "@type": "@id",
                  "@context": {
                    "hadRole": {
                      "@id": "prov:hadRole",
                      "@type": "@id"
                    },
                    "hadPlan": {
                      "@id": "prov:hadPlan",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "agent": {
              "@id": "prov:agent",
              "@type": "@id"
            }
          }
        }
      }
    },
    "wasQuotedFrom": {
      "@id": "prov:wasQuotedFrom",
      "@type": "@id",
      "@context": {
        "actedOnBehalfOf": {
          "@id": "prov:actedOnBehalfOf",
          "@type": "@id"
        },
        "qualifiedDelegation": {
          "@id": "prov:qualifiedDelegation",
          "@type": "@id",
          "@context": {
            "agent": {
              "@id": "prov:agent",
              "@type": "@id"
            },
            "hadActivity": {
              "@id": "prov:hadActivity",
              "@type": "@id",
              "@context": {
                "wasAssociatedWith": {
                  "@id": "prov:wasAssociatedWith",
                  "@type": "@id"
                },
                "used": {
                  "@id": "prov:used",
                  "@type": "@id"
                },
                "wasStartedBy": {
                  "@id": "prov:wasStartedBy",
                  "@type": "@id"
                },
                "wasEndedBy": {
                  "@id": "prov:wasEndedBy",
                  "@type": "@id"
                },
                "invalidated": {
                  "@id": "prov:invalidated",
                  "@type": "@id"
                },
                "generated": {
                  "@id": "prov:generated",
                  "@type": "@id"
                },
                "qualifiedUsage": {
                  "@id": "prov:qualifiedUsage",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedStart": {
                  "@id": "prov:qualifiedStart",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedEnd": {
                  "@id": "prov:qualifiedEnd",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedAssociation": {
                  "@id": "prov:qualifiedAssociation",
                  "@type": "@id",
                  "@context": {
                    "hadRole": {
                      "@id": "prov:hadRole",
                      "@type": "@id"
                    },
                    "hadPlan": {
                      "@id": "prov:hadPlan",
                      "@type": "@id"
                    }
                  }
                },
                "wasInfluencedBy": {
                  "@id": "prov:wasInfluencedBy",
                  "@type": "@id"
                },
                "qualifiedInfluence": {
                  "@id": "prov:qualifiedInfluence",
                  "@type": "@id",
                  "@context": {
                    "influencer": {
                      "@id": "prov:influencer",
                      "@type": "@id"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    }
                  }
                }
              }
            }
          }
        },
        "wasInfluencedBy": {
          "@id": "prov:wasInfluencedBy",
          "@type": "@id",
          "@context": {
            "wasAssociatedWith": {
              "@id": "prov:wasAssociatedWith",
              "@type": "@id"
            },
            "used": {
              "@id": "prov:used",
              "@type": "@id"
            },
            "wasStartedBy": {
              "@id": "prov:wasStartedBy",
              "@type": "@id"
            },
            "wasEndedBy": {
              "@id": "prov:wasEndedBy",
              "@type": "@id"
            },
            "invalidated": {
              "@id": "prov:invalidated",
              "@type": "@id"
            },
            "generated": {
              "@id": "prov:generated",
              "@type": "@id"
            },
            "qualifiedUsage": {
              "@id": "prov:qualifiedUsage",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedStart": {
              "@id": "prov:qualifiedStart",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedEnd": {
              "@id": "prov:qualifiedEnd",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedAssociation": {
              "@id": "prov:qualifiedAssociation",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                },
                "hadRole": {
                  "@id": "prov:hadRole",
                  "@type": "@id"
                },
                "hadPlan": {
                  "@id": "prov:hadPlan",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "qualifiedInfluence": {
          "@id": "prov:qualifiedInfluence",
          "@type": "@id",
          "@context": {
            "influencer": {
              "@id": "prov:influencer",
              "@type": "@id",
              "@context": {
                "wasAssociatedWith": {
                  "@id": "prov:wasAssociatedWith",
                  "@type": "@id"
                },
                "used": {
                  "@id": "prov:used",
                  "@type": "@id"
                },
                "wasStartedBy": {
                  "@id": "prov:wasStartedBy",
                  "@type": "@id"
                },
                "wasEndedBy": {
                  "@id": "prov:wasEndedBy",
                  "@type": "@id"
                },
                "invalidated": {
                  "@id": "prov:invalidated",
                  "@type": "@id"
                },
                "generated": {
                  "@id": "prov:generated",
                  "@type": "@id"
                },
                "qualifiedUsage": {
                  "@id": "prov:qualifiedUsage",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    }
                  }
                },
                "qualifiedStart": {
                  "@id": "prov:qualifiedStart",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedEnd": {
                  "@id": "prov:qualifiedEnd",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedAssociation": {
                  "@id": "prov:qualifiedAssociation",
                  "@type": "@id",
                  "@context": {
                    "hadRole": {
                      "@id": "prov:hadRole",
                      "@type": "@id"
                    },
                    "hadPlan": {
                      "@id": "prov:hadPlan",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "entity": {
              "@id": "prov:entity",
              "@type": "@id"
            },
            "activity": {
              "@id": "prov:activity",
              "@type": "@id",
              "@context": {
                "wasAssociatedWith": {
                  "@id": "prov:wasAssociatedWith",
                  "@type": "@id"
                },
                "used": {
                  "@id": "prov:used",
                  "@type": "@id"
                },
                "wasStartedBy": {
                  "@id": "prov:wasStartedBy",
                  "@type": "@id"
                },
                "wasEndedBy": {
                  "@id": "prov:wasEndedBy",
                  "@type": "@id"
                },
                "invalidated": {
                  "@id": "prov:invalidated",
                  "@type": "@id"
                },
                "generated": {
                  "@id": "prov:generated",
                  "@type": "@id"
                },
                "qualifiedUsage": {
                  "@id": "prov:qualifiedUsage",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    }
                  }
                },
                "qualifiedStart": {
                  "@id": "prov:qualifiedStart",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedEnd": {
                  "@id": "prov:qualifiedEnd",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedAssociation": {
                  "@id": "prov:qualifiedAssociation",
                  "@type": "@id",
                  "@context": {
                    "hadRole": {
                      "@id": "prov:hadRole",
                      "@type": "@id"
                    },
                    "hadPlan": {
                      "@id": "prov:hadPlan",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "agent": {
              "@id": "prov:agent",
              "@type": "@id"
            }
          }
        }
      }
    },
    "wasRevisionOf": {
      "@id": "prov:wasRevisionOf",
      "@type": "@id",
      "@context": {
        "actedOnBehalfOf": {
          "@id": "prov:actedOnBehalfOf",
          "@type": "@id"
        },
        "qualifiedDelegation": {
          "@id": "prov:qualifiedDelegation",
          "@type": "@id",
          "@context": {
            "agent": {
              "@id": "prov:agent",
              "@type": "@id"
            },
            "hadActivity": {
              "@id": "prov:hadActivity",
              "@type": "@id",
              "@context": {
                "wasAssociatedWith": {
                  "@id": "prov:wasAssociatedWith",
                  "@type": "@id"
                },
                "used": {
                  "@id": "prov:used",
                  "@type": "@id"
                },
                "wasStartedBy": {
                  "@id": "prov:wasStartedBy",
                  "@type": "@id"
                },
                "wasEndedBy": {
                  "@id": "prov:wasEndedBy",
                  "@type": "@id"
                },
                "invalidated": {
                  "@id": "prov:invalidated",
                  "@type": "@id"
                },
                "generated": {
                  "@id": "prov:generated",
                  "@type": "@id"
                },
                "qualifiedUsage": {
                  "@id": "prov:qualifiedUsage",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedStart": {
                  "@id": "prov:qualifiedStart",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedEnd": {
                  "@id": "prov:qualifiedEnd",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedAssociation": {
                  "@id": "prov:qualifiedAssociation",
                  "@type": "@id",
                  "@context": {
                    "hadRole": {
                      "@id": "prov:hadRole",
                      "@type": "@id"
                    },
                    "hadPlan": {
                      "@id": "prov:hadPlan",
                      "@type": "@id"
                    }
                  }
                },
                "wasInfluencedBy": {
                  "@id": "prov:wasInfluencedBy",
                  "@type": "@id"
                },
                "qualifiedInfluence": {
                  "@id": "prov:qualifiedInfluence",
                  "@type": "@id",
                  "@context": {
                    "influencer": {
                      "@id": "prov:influencer",
                      "@type": "@id"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    }
                  }
                }
              }
            }
          }
        },
        "wasInfluencedBy": {
          "@id": "prov:wasInfluencedBy",
          "@type": "@id",
          "@context": {
            "wasAssociatedWith": {
              "@id": "prov:wasAssociatedWith",
              "@type": "@id"
            },
            "used": {
              "@id": "prov:used",
              "@type": "@id"
            },
            "wasStartedBy": {
              "@id": "prov:wasStartedBy",
              "@type": "@id"
            },
            "wasEndedBy": {
              "@id": "prov:wasEndedBy",
              "@type": "@id"
            },
            "invalidated": {
              "@id": "prov:invalidated",
              "@type": "@id"
            },
            "generated": {
              "@id": "prov:generated",
              "@type": "@id"
            },
            "qualifiedUsage": {
              "@id": "prov:qualifiedUsage",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedStart": {
              "@id": "prov:qualifiedStart",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedEnd": {
              "@id": "prov:qualifiedEnd",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedAssociation": {
              "@id": "prov:qualifiedAssociation",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                },
                "hadRole": {
                  "@id": "prov:hadRole",
                  "@type": "@id"
                },
                "hadPlan": {
                  "@id": "prov:hadPlan",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "qualifiedInfluence": {
          "@id": "prov:qualifiedInfluence",
          "@type": "@id",
          "@context": {
            "influencer": {
              "@id": "prov:influencer",
              "@type": "@id",
              "@context": {
                "wasAssociatedWith": {
                  "@id": "prov:wasAssociatedWith",
                  "@type": "@id"
                },
                "used": {
                  "@id": "prov:used",
                  "@type": "@id"
                },
                "wasStartedBy": {
                  "@id": "prov:wasStartedBy",
                  "@type": "@id"
                },
                "wasEndedBy": {
                  "@id": "prov:wasEndedBy",
                  "@type": "@id"
                },
                "invalidated": {
                  "@id": "prov:invalidated",
                  "@type": "@id"
                },
                "generated": {
                  "@id": "prov:generated",
                  "@type": "@id"
                },
                "qualifiedUsage": {
                  "@id": "prov:qualifiedUsage",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    }
                  }
                },
                "qualifiedStart": {
                  "@id": "prov:qualifiedStart",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedEnd": {
                  "@id": "prov:qualifiedEnd",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedAssociation": {
                  "@id": "prov:qualifiedAssociation",
                  "@type": "@id",
                  "@context": {
                    "hadRole": {
                      "@id": "prov:hadRole",
                      "@type": "@id"
                    },
                    "hadPlan": {
                      "@id": "prov:hadPlan",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "entity": {
              "@id": "prov:entity",
              "@type": "@id"
            },
            "activity": {
              "@id": "prov:activity",
              "@type": "@id",
              "@context": {
                "wasAssociatedWith": {
                  "@id": "prov:wasAssociatedWith",
                  "@type": "@id"
                },
                "used": {
                  "@id": "prov:used",
                  "@type": "@id"
                },
                "wasStartedBy": {
                  "@id": "prov:wasStartedBy",
                  "@type": "@id"
                },
                "wasEndedBy": {
                  "@id": "prov:wasEndedBy",
                  "@type": "@id"
                },
                "invalidated": {
                  "@id": "prov:invalidated",
                  "@type": "@id"
                },
                "generated": {
                  "@id": "prov:generated",
                  "@type": "@id"
                },
                "qualifiedUsage": {
                  "@id": "prov:qualifiedUsage",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    }
                  }
                },
                "qualifiedStart": {
                  "@id": "prov:qualifiedStart",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedEnd": {
                  "@id": "prov:qualifiedEnd",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedAssociation": {
                  "@id": "prov:qualifiedAssociation",
                  "@type": "@id",
                  "@context": {
                    "hadRole": {
                      "@id": "prov:hadRole",
                      "@type": "@id"
                    },
                    "hadPlan": {
                      "@id": "prov:hadPlan",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "agent": {
              "@id": "prov:agent",
              "@type": "@id"
            }
          }
        }
      }
    },
    "mentionOf": {
      "@id": "prov:mentionOf",
      "@type": "@id",
      "@context": {
        "actedOnBehalfOf": {
          "@id": "prov:actedOnBehalfOf",
          "@type": "@id"
        },
        "qualifiedDelegation": {
          "@id": "prov:qualifiedDelegation",
          "@type": "@id",
          "@context": {
            "agent": {
              "@id": "prov:agent",
              "@type": "@id"
            },
            "hadActivity": {
              "@id": "prov:hadActivity",
              "@type": "@id",
              "@context": {
                "wasAssociatedWith": {
                  "@id": "prov:wasAssociatedWith",
                  "@type": "@id"
                },
                "used": {
                  "@id": "prov:used",
                  "@type": "@id"
                },
                "wasStartedBy": {
                  "@id": "prov:wasStartedBy",
                  "@type": "@id"
                },
                "wasEndedBy": {
                  "@id": "prov:wasEndedBy",
                  "@type": "@id"
                },
                "invalidated": {
                  "@id": "prov:invalidated",
                  "@type": "@id"
                },
                "generated": {
                  "@id": "prov:generated",
                  "@type": "@id"
                },
                "qualifiedUsage": {
                  "@id": "prov:qualifiedUsage",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedStart": {
                  "@id": "prov:qualifiedStart",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedEnd": {
                  "@id": "prov:qualifiedEnd",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedAssociation": {
                  "@id": "prov:qualifiedAssociation",
                  "@type": "@id",
                  "@context": {
                    "hadRole": {
                      "@id": "prov:hadRole",
                      "@type": "@id"
                    },
                    "hadPlan": {
                      "@id": "prov:hadPlan",
                      "@type": "@id"
                    }
                  }
                },
                "wasInfluencedBy": {
                  "@id": "prov:wasInfluencedBy",
                  "@type": "@id"
                },
                "qualifiedInfluence": {
                  "@id": "prov:qualifiedInfluence",
                  "@type": "@id",
                  "@context": {
                    "influencer": {
                      "@id": "prov:influencer",
                      "@type": "@id"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    }
                  }
                }
              }
            }
          }
        },
        "wasInfluencedBy": {
          "@id": "prov:wasInfluencedBy",
          "@type": "@id",
          "@context": {
            "wasAssociatedWith": {
              "@id": "prov:wasAssociatedWith",
              "@type": "@id"
            },
            "used": {
              "@id": "prov:used",
              "@type": "@id"
            },
            "wasStartedBy": {
              "@id": "prov:wasStartedBy",
              "@type": "@id"
            },
            "wasEndedBy": {
              "@id": "prov:wasEndedBy",
              "@type": "@id"
            },
            "invalidated": {
              "@id": "prov:invalidated",
              "@type": "@id"
            },
            "generated": {
              "@id": "prov:generated",
              "@type": "@id"
            },
            "qualifiedUsage": {
              "@id": "prov:qualifiedUsage",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedStart": {
              "@id": "prov:qualifiedStart",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedEnd": {
              "@id": "prov:qualifiedEnd",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedAssociation": {
              "@id": "prov:qualifiedAssociation",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                },
                "hadRole": {
                  "@id": "prov:hadRole",
                  "@type": "@id"
                },
                "hadPlan": {
                  "@id": "prov:hadPlan",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "qualifiedInfluence": {
          "@id": "prov:qualifiedInfluence",
          "@type": "@id",
          "@context": {
            "influencer": {
              "@id": "prov:influencer",
              "@type": "@id",
              "@context": {
                "wasAssociatedWith": {
                  "@id": "prov:wasAssociatedWith",
                  "@type": "@id"
                },
                "used": {
                  "@id": "prov:used",
                  "@type": "@id"
                },
                "wasStartedBy": {
                  "@id": "prov:wasStartedBy",
                  "@type": "@id"
                },
                "wasEndedBy": {
                  "@id": "prov:wasEndedBy",
                  "@type": "@id"
                },
                "invalidated": {
                  "@id": "prov:invalidated",
                  "@type": "@id"
                },
                "generated": {
                  "@id": "prov:generated",
                  "@type": "@id"
                },
                "qualifiedUsage": {
                  "@id": "prov:qualifiedUsage",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    }
                  }
                },
                "qualifiedStart": {
                  "@id": "prov:qualifiedStart",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedEnd": {
                  "@id": "prov:qualifiedEnd",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedAssociation": {
                  "@id": "prov:qualifiedAssociation",
                  "@type": "@id",
                  "@context": {
                    "hadRole": {
                      "@id": "prov:hadRole",
                      "@type": "@id"
                    },
                    "hadPlan": {
                      "@id": "prov:hadPlan",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "entity": {
              "@id": "prov:entity",
              "@type": "@id"
            },
            "activity": {
              "@id": "prov:activity",
              "@type": "@id",
              "@context": {
                "wasAssociatedWith": {
                  "@id": "prov:wasAssociatedWith",
                  "@type": "@id"
                },
                "used": {
                  "@id": "prov:used",
                  "@type": "@id"
                },
                "wasStartedBy": {
                  "@id": "prov:wasStartedBy",
                  "@type": "@id"
                },
                "wasEndedBy": {
                  "@id": "prov:wasEndedBy",
                  "@type": "@id"
                },
                "invalidated": {
                  "@id": "prov:invalidated",
                  "@type": "@id"
                },
                "generated": {
                  "@id": "prov:generated",
                  "@type": "@id"
                },
                "qualifiedUsage": {
                  "@id": "prov:qualifiedUsage",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    }
                  }
                },
                "qualifiedStart": {
                  "@id": "prov:qualifiedStart",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedEnd": {
                  "@id": "prov:qualifiedEnd",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedAssociation": {
                  "@id": "prov:qualifiedAssociation",
                  "@type": "@id",
                  "@context": {
                    "hadRole": {
                      "@id": "prov:hadRole",
                      "@type": "@id"
                    },
                    "hadPlan": {
                      "@id": "prov:hadPlan",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "agent": {
              "@id": "prov:agent",
              "@type": "@id"
            }
          }
        }
      }
    },
    "href": "oa:hasTarget",
    "rel": {
      "@id": "http://www.iana.org/assignments/relation",
      "@type": "@id",
      "@context": {
        "@base": "http://www.iana.org/assignments/relation/"
      }
    },
    "type": "dct:type",
    "hreflang": "dct:language",
    "title": "rdfs:label",
    "length": "dct:extent",
    "qualifiedGeneration": {
      "@id": "prov:qualifiedGeneration",
      "@type": "@id",
      "@context": {
        "atTime": {
          "@id": "prov:atTime",
          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
        },
        "activity": {
          "@id": "prov:activity",
          "@type": "@id",
          "@context": {
            "wasAssociatedWith": {
              "@id": "prov:wasAssociatedWith",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                },
                "qualifiedDelegation": {
                  "@id": "prov:qualifiedDelegation",
                  "@type": "@id",
                  "@context": {
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "wasInfluencedBy": {
                  "@id": "prov:wasInfluencedBy",
                  "@type": "@id"
                },
                "qualifiedInfluence": {
                  "@id": "prov:qualifiedInfluence",
                  "@type": "@id",
                  "@context": {
                    "influencer": {
                      "@id": "prov:influencer",
                      "@type": "@id"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    },
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "used": {
              "@id": "prov:used",
              "@type": "@id"
            },
            "wasStartedBy": {
              "@id": "prov:wasStartedBy",
              "@type": "@id"
            },
            "wasEndedBy": {
              "@id": "prov:wasEndedBy",
              "@type": "@id"
            },
            "invalidated": {
              "@id": "prov:invalidated",
              "@type": "@id"
            },
            "generated": {
              "@id": "prov:generated",
              "@type": "@id"
            },
            "qualifiedUsage": {
              "@id": "prov:qualifiedUsage",
              "@type": "@id",
              "@context": {
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedCommunication": {
              "@id": "prov:qualifiedCommunication",
              "@type": "@id",
              "@context": {
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedStart": {
              "@id": "prov:qualifiedStart",
              "@type": "@id",
              "@context": {
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedEnd": {
              "@id": "prov:qualifiedEnd",
              "@type": "@id",
              "@context": {
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedAssociation": {
              "@id": "prov:qualifiedAssociation",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id",
                  "@context": {
                    "qualifiedDelegation": {
                      "@id": "prov:qualifiedDelegation",
                      "@type": "@id",
                      "@context": {
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    },
                    "wasInfluencedBy": {
                      "@id": "prov:wasInfluencedBy",
                      "@type": "@id",
                      "@context": {}
                    },
                    "qualifiedInfluence": {
                      "@id": "prov:qualifiedInfluence",
                      "@type": "@id",
                      "@context": {
                        "influencer": {
                          "@id": "prov:influencer",
                          "@type": "@id",
                          "@context": {}
                        },
                        "entity": {
                          "@id": "prov:entity",
                          "@type": "@id"
                        },
                        "activity": {
                          "@id": "prov:activity",
                          "@type": "@id"
                        },
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id",
                          "@context": {}
                        }
                      }
                    }
                  }
                },
                "hadRole": {
                  "@id": "prov:hadRole",
                  "@type": "@id"
                },
                "hadPlan": {
                  "@id": "prov:hadPlan",
                  "@type": "@id"
                }
              }
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                },
                "qualifiedDelegation": {
                  "@id": "prov:qualifiedDelegation",
                  "@type": "@id",
                  "@context": {
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id",
                  "@context": {
                    "actedOnBehalfOf": {
                      "@id": "prov:actedOnBehalfOf",
                      "@type": "@id"
                    },
                    "qualifiedDelegation": {
                      "@id": "prov:qualifiedDelegation",
                      "@type": "@id",
                      "@context": {
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id",
                  "@context": {
                    "actedOnBehalfOf": {
                      "@id": "prov:actedOnBehalfOf",
                      "@type": "@id"
                    },
                    "qualifiedDelegation": {
                      "@id": "prov:qualifiedDelegation",
                      "@type": "@id",
                      "@context": {
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                }
              }
            }
          }
        }
      }
    },
    "qualifiedInvalidation": {
      "@id": "prov:qualifiedInvalidation",
      "@type": "@id",
      "@context": {
        "atTime": {
          "@id": "prov:atTime",
          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
        },
        "activity": {
          "@id": "prov:activity",
          "@type": "@id",
          "@context": {
            "wasAssociatedWith": {
              "@id": "prov:wasAssociatedWith",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                },
                "qualifiedDelegation": {
                  "@id": "prov:qualifiedDelegation",
                  "@type": "@id",
                  "@context": {
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "wasInfluencedBy": {
                  "@id": "prov:wasInfluencedBy",
                  "@type": "@id"
                },
                "qualifiedInfluence": {
                  "@id": "prov:qualifiedInfluence",
                  "@type": "@id",
                  "@context": {
                    "influencer": {
                      "@id": "prov:influencer",
                      "@type": "@id"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    },
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "used": {
              "@id": "prov:used",
              "@type": "@id"
            },
            "wasStartedBy": {
              "@id": "prov:wasStartedBy",
              "@type": "@id"
            },
            "wasEndedBy": {
              "@id": "prov:wasEndedBy",
              "@type": "@id"
            },
            "invalidated": {
              "@id": "prov:invalidated",
              "@type": "@id"
            },
            "generated": {
              "@id": "prov:generated",
              "@type": "@id"
            },
            "qualifiedUsage": {
              "@id": "prov:qualifiedUsage",
              "@type": "@id",
              "@context": {
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedCommunication": {
              "@id": "prov:qualifiedCommunication",
              "@type": "@id",
              "@context": {
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedStart": {
              "@id": "prov:qualifiedStart",
              "@type": "@id",
              "@context": {
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedEnd": {
              "@id": "prov:qualifiedEnd",
              "@type": "@id",
              "@context": {
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedAssociation": {
              "@id": "prov:qualifiedAssociation",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id",
                  "@context": {
                    "qualifiedDelegation": {
                      "@id": "prov:qualifiedDelegation",
                      "@type": "@id",
                      "@context": {
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    },
                    "wasInfluencedBy": {
                      "@id": "prov:wasInfluencedBy",
                      "@type": "@id",
                      "@context": {}
                    },
                    "qualifiedInfluence": {
                      "@id": "prov:qualifiedInfluence",
                      "@type": "@id",
                      "@context": {
                        "influencer": {
                          "@id": "prov:influencer",
                          "@type": "@id",
                          "@context": {}
                        },
                        "entity": {
                          "@id": "prov:entity",
                          "@type": "@id"
                        },
                        "activity": {
                          "@id": "prov:activity",
                          "@type": "@id"
                        },
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id",
                          "@context": {}
                        }
                      }
                    }
                  }
                },
                "hadRole": {
                  "@id": "prov:hadRole",
                  "@type": "@id"
                },
                "hadPlan": {
                  "@id": "prov:hadPlan",
                  "@type": "@id"
                }
              }
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                },
                "qualifiedDelegation": {
                  "@id": "prov:qualifiedDelegation",
                  "@type": "@id",
                  "@context": {
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id",
                  "@context": {
                    "actedOnBehalfOf": {
                      "@id": "prov:actedOnBehalfOf",
                      "@type": "@id"
                    },
                    "qualifiedDelegation": {
                      "@id": "prov:qualifiedDelegation",
                      "@type": "@id",
                      "@context": {
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id",
                  "@context": {
                    "actedOnBehalfOf": {
                      "@id": "prov:actedOnBehalfOf",
                      "@type": "@id"
                    },
                    "qualifiedDelegation": {
                      "@id": "prov:qualifiedDelegation",
                      "@type": "@id",
                      "@context": {
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                }
              }
            }
          }
        }
      }
    },
    "qualifiedDerivation": {
      "@id": "prov:qualifiedDerivation",
      "@type": "@id",
      "@context": {
        "hadGeneration": {
          "@id": "prov:hadGeneration",
          "@type": "@id",
          "@context": {
            "atTime": {
              "@id": "prov:atTime",
              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
            },
            "activity": {
              "@id": "prov:activity",
              "@type": "@id",
              "@context": {
                "wasAssociatedWith": {
                  "@id": "prov:wasAssociatedWith",
                  "@type": "@id",
                  "@context": {
                    "actedOnBehalfOf": {
                      "@id": "prov:actedOnBehalfOf",
                      "@type": "@id"
                    },
                    "qualifiedDelegation": {
                      "@id": "prov:qualifiedDelegation",
                      "@type": "@id",
                      "@context": {
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    },
                    "wasInfluencedBy": {
                      "@id": "prov:wasInfluencedBy",
                      "@type": "@id"
                    },
                    "qualifiedInfluence": {
                      "@id": "prov:qualifiedInfluence",
                      "@type": "@id",
                      "@context": {
                        "influencer": {
                          "@id": "prov:influencer",
                          "@type": "@id"
                        },
                        "activity": {
                          "@id": "prov:activity",
                          "@type": "@id"
                        },
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                },
                "used": {
                  "@id": "prov:used",
                  "@type": "@id"
                },
                "wasStartedBy": {
                  "@id": "prov:wasStartedBy",
                  "@type": "@id"
                },
                "wasEndedBy": {
                  "@id": "prov:wasEndedBy",
                  "@type": "@id"
                },
                "invalidated": {
                  "@id": "prov:invalidated",
                  "@type": "@id"
                },
                "generated": {
                  "@id": "prov:generated",
                  "@type": "@id"
                },
                "qualifiedUsage": {
                  "@id": "prov:qualifiedUsage",
                  "@type": "@id",
                  "@context": {}
                },
                "qualifiedCommunication": {
                  "@id": "prov:qualifiedCommunication",
                  "@type": "@id",
                  "@context": {
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedStart": {
                  "@id": "prov:qualifiedStart",
                  "@type": "@id",
                  "@context": {
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedEnd": {
                  "@id": "prov:qualifiedEnd",
                  "@type": "@id",
                  "@context": {
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedAssociation": {
                  "@id": "prov:qualifiedAssociation",
                  "@type": "@id",
                  "@context": {
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id",
                      "@context": {
                        "qualifiedDelegation": {
                          "@id": "prov:qualifiedDelegation",
                          "@type": "@id",
                          "@context": {
                            "agent": {
                              "@id": "prov:agent",
                              "@type": "@id"
                            },
                            "hadActivity": {
                              "@id": "prov:hadActivity",
                              "@type": "@id"
                            }
                          }
                        },
                        "wasInfluencedBy": {
                          "@id": "prov:wasInfluencedBy",
                          "@type": "@id",
                          "@context": {}
                        },
                        "qualifiedInfluence": {
                          "@id": "prov:qualifiedInfluence",
                          "@type": "@id",
                          "@context": {
                            "influencer": {
                              "@id": "prov:influencer",
                              "@type": "@id",
                              "@context": {}
                            },
                            "activity": {
                              "@id": "prov:activity",
                              "@type": "@id"
                            },
                            "agent": {
                              "@id": "prov:agent",
                              "@type": "@id",
                              "@context": {}
                            }
                          }
                        }
                      }
                    },
                    "hadRole": {
                      "@id": "prov:hadRole",
                      "@type": "@id"
                    },
                    "hadPlan": {
                      "@id": "prov:hadPlan",
                      "@type": "@id"
                    }
                  }
                },
                "wasInfluencedBy": {
                  "@id": "prov:wasInfluencedBy",
                  "@type": "@id",
                  "@context": {
                    "actedOnBehalfOf": {
                      "@id": "prov:actedOnBehalfOf",
                      "@type": "@id"
                    },
                    "qualifiedDelegation": {
                      "@id": "prov:qualifiedDelegation",
                      "@type": "@id",
                      "@context": {
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                },
                "qualifiedInfluence": {
                  "@id": "prov:qualifiedInfluence",
                  "@type": "@id",
                  "@context": {
                    "influencer": {
                      "@id": "prov:influencer",
                      "@type": "@id",
                      "@context": {
                        "actedOnBehalfOf": {
                          "@id": "prov:actedOnBehalfOf",
                          "@type": "@id"
                        },
                        "qualifiedDelegation": {
                          "@id": "prov:qualifiedDelegation",
                          "@type": "@id",
                          "@context": {
                            "agent": {
                              "@id": "prov:agent",
                              "@type": "@id"
                            },
                            "hadActivity": {
                              "@id": "prov:hadActivity",
                              "@type": "@id"
                            }
                          }
                        }
                      }
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    },
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id",
                      "@context": {
                        "actedOnBehalfOf": {
                          "@id": "prov:actedOnBehalfOf",
                          "@type": "@id"
                        },
                        "qualifiedDelegation": {
                          "@id": "prov:qualifiedDelegation",
                          "@type": "@id",
                          "@context": {
                            "agent": {
                              "@id": "prov:agent",
                              "@type": "@id"
                            },
                            "hadActivity": {
                              "@id": "prov:hadActivity",
                              "@type": "@id"
                            }
                          }
                        }
                      }
                    }
                  }
                }
              }
            }
          }
        },
        "hadActivity": {
          "@id": "prov:hadActivity",
          "@type": "@id",
          "@context": {
            "wasAssociatedWith": {
              "@id": "prov:wasAssociatedWith",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                },
                "qualifiedDelegation": {
                  "@id": "prov:qualifiedDelegation",
                  "@type": "@id",
                  "@context": {
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "wasInfluencedBy": {
                  "@id": "prov:wasInfluencedBy",
                  "@type": "@id"
                },
                "qualifiedInfluence": {
                  "@id": "prov:qualifiedInfluence",
                  "@type": "@id",
                  "@context": {
                    "influencer": {
                      "@id": "prov:influencer",
                      "@type": "@id"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    },
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "used": {
              "@id": "prov:used",
              "@type": "@id"
            },
            "wasStartedBy": {
              "@id": "prov:wasStartedBy",
              "@type": "@id"
            },
            "wasEndedBy": {
              "@id": "prov:wasEndedBy",
              "@type": "@id"
            },
            "invalidated": {
              "@id": "prov:invalidated",
              "@type": "@id"
            },
            "generated": {
              "@id": "prov:generated",
              "@type": "@id"
            },
            "qualifiedUsage": {
              "@id": "prov:qualifiedUsage",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                }
              }
            },
            "qualifiedStart": {
              "@id": "prov:qualifiedStart",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedEnd": {
              "@id": "prov:qualifiedEnd",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              }
            },
            "qualifiedAssociation": {
              "@id": "prov:qualifiedAssociation",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id",
                  "@context": {
                    "qualifiedDelegation": {
                      "@id": "prov:qualifiedDelegation",
                      "@type": "@id",
                      "@context": {
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    },
                    "wasInfluencedBy": {
                      "@id": "prov:wasInfluencedBy",
                      "@type": "@id",
                      "@context": {}
                    },
                    "qualifiedInfluence": {
                      "@id": "prov:qualifiedInfluence",
                      "@type": "@id",
                      "@context": {
                        "influencer": {
                          "@id": "prov:influencer",
                          "@type": "@id",
                          "@context": {}
                        },
                        "activity": {
                          "@id": "prov:activity",
                          "@type": "@id"
                        },
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id",
                          "@context": {}
                        }
                      }
                    }
                  }
                },
                "hadRole": {
                  "@id": "prov:hadRole",
                  "@type": "@id"
                },
                "hadPlan": {
                  "@id": "prov:hadPlan",
                  "@type": "@id"
                }
              }
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                },
                "qualifiedDelegation": {
                  "@id": "prov:qualifiedDelegation",
                  "@type": "@id",
                  "@context": {
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id",
                  "@context": {
                    "actedOnBehalfOf": {
                      "@id": "prov:actedOnBehalfOf",
                      "@type": "@id"
                    },
                    "qualifiedDelegation": {
                      "@id": "prov:qualifiedDelegation",
                      "@type": "@id",
                      "@context": {
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id",
                  "@context": {
                    "actedOnBehalfOf": {
                      "@id": "prov:actedOnBehalfOf",
                      "@type": "@id"
                    },
                    "qualifiedDelegation": {
                      "@id": "prov:qualifiedDelegation",
                      "@type": "@id",
                      "@context": {
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                }
              }
            }
          }
        },
        "hadUsage": {
          "@id": "prov:hadUsage",
          "@type": "@id",
          "@context": {
            "atTime": {
              "@id": "prov:atTime",
              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
            }
          }
        },
        "entity": {
          "@id": "prov:entity",
          "@type": "@id"
        }
      }
    },
    "qualifiedAttribution": {
      "@id": "prov:qualifiedAttribution",
      "@type": "@id",
      "@context": {
        "agent": {
          "@id": "prov:agent",
          "@type": "@id",
          "@context": {
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id",
              "@context": {
                "wasAssociatedWith": {
                  "@id": "prov:wasAssociatedWith",
                  "@type": "@id",
                  "@context": {}
                },
                "used": {
                  "@id": "prov:used",
                  "@type": "@id"
                },
                "wasStartedBy": {
                  "@id": "prov:wasStartedBy",
                  "@type": "@id"
                },
                "wasEndedBy": {
                  "@id": "prov:wasEndedBy",
                  "@type": "@id"
                },
                "invalidated": {
                  "@id": "prov:invalidated",
                  "@type": "@id"
                },
                "generated": {
                  "@id": "prov:generated",
                  "@type": "@id"
                },
                "qualifiedUsage": {
                  "@id": "prov:qualifiedUsage",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedStart": {
                  "@id": "prov:qualifiedStart",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedEnd": {
                  "@id": "prov:qualifiedEnd",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedAssociation": {
                  "@id": "prov:qualifiedAssociation",
                  "@type": "@id",
                  "@context": {
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    },
                    "hadRole": {
                      "@id": "prov:hadRole",
                      "@type": "@id"
                    },
                    "hadPlan": {
                      "@id": "prov:hadPlan",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id",
                  "@context": {
                    "wasAssociatedWith": {
                      "@id": "prov:wasAssociatedWith",
                      "@type": "@id",
                      "@context": {}
                    },
                    "used": {
                      "@id": "prov:used",
                      "@type": "@id"
                    },
                    "wasStartedBy": {
                      "@id": "prov:wasStartedBy",
                      "@type": "@id"
                    },
                    "wasEndedBy": {
                      "@id": "prov:wasEndedBy",
                      "@type": "@id"
                    },
                    "invalidated": {
                      "@id": "prov:invalidated",
                      "@type": "@id"
                    },
                    "generated": {
                      "@id": "prov:generated",
                      "@type": "@id"
                    },
                    "qualifiedUsage": {
                      "@id": "prov:qualifiedUsage",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        }
                      }
                    },
                    "qualifiedStart": {
                      "@id": "prov:qualifiedStart",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    },
                    "qualifiedEnd": {
                      "@id": "prov:qualifiedEnd",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    },
                    "qualifiedAssociation": {
                      "@id": "prov:qualifiedAssociation",
                      "@type": "@id",
                      "@context": {
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id"
                        },
                        "hadRole": {
                          "@id": "prov:hadRole",
                          "@type": "@id"
                        },
                        "hadPlan": {
                          "@id": "prov:hadPlan",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id",
                  "@context": {
                    "wasAssociatedWith": {
                      "@id": "prov:wasAssociatedWith",
                      "@type": "@id",
                      "@context": {}
                    },
                    "used": {
                      "@id": "prov:used",
                      "@type": "@id"
                    },
                    "wasStartedBy": {
                      "@id": "prov:wasStartedBy",
                      "@type": "@id"
                    },
                    "wasEndedBy": {
                      "@id": "prov:wasEndedBy",
                      "@type": "@id"
                    },
                    "invalidated": {
                      "@id": "prov:invalidated",
                      "@type": "@id"
                    },
                    "generated": {
                      "@id": "prov:generated",
                      "@type": "@id"
                    },
                    "qualifiedUsage": {
                      "@id": "prov:qualifiedUsage",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        }
                      }
                    },
                    "qualifiedStart": {
                      "@id": "prov:qualifiedStart",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    },
                    "qualifiedEnd": {
                      "@id": "prov:qualifiedEnd",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    },
                    "qualifiedAssociation": {
                      "@id": "prov:qualifiedAssociation",
                      "@type": "@id",
                      "@context": {
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id"
                        },
                        "hadRole": {
                          "@id": "prov:hadRole",
                          "@type": "@id"
                        },
                        "hadPlan": {
                          "@id": "prov:hadPlan",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id",
                  "@context": {}
                }
              }
            }
          }
        }
      }
    },
    "hadMember": {
      "@id": "prov:hadMember",
      "@type": "@id",
      "@context": {
        "wasAssociatedWith": {
          "@id": "prov:wasAssociatedWith",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "qualifiedDelegation": {
              "@id": "prov:qualifiedDelegation",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              }
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id"
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id"
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "used": {
          "@id": "prov:used",
          "@type": "@id"
        },
        "wasStartedBy": {
          "@id": "prov:wasStartedBy",
          "@type": "@id"
        },
        "wasEndedBy": {
          "@id": "prov:wasEndedBy",
          "@type": "@id"
        },
        "invalidated": {
          "@id": "prov:invalidated",
          "@type": "@id"
        },
        "generated": {
          "@id": "prov:generated",
          "@type": "@id"
        },
        "qualifiedUsage": {
          "@id": "prov:qualifiedUsage",
          "@type": "@id",
          "@context": {
            "atTime": {
              "@id": "prov:atTime",
              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
            },
            "entity": {
              "@id": "prov:entity",
              "@type": "@id"
            }
          }
        },
        "qualifiedStart": {
          "@id": "prov:qualifiedStart",
          "@type": "@id",
          "@context": {
            "atTime": {
              "@id": "prov:atTime",
              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
            },
            "entity": {
              "@id": "prov:entity",
              "@type": "@id"
            },
            "hadActivity": {
              "@id": "prov:hadActivity",
              "@type": "@id"
            }
          }
        },
        "qualifiedEnd": {
          "@id": "prov:qualifiedEnd",
          "@type": "@id",
          "@context": {
            "atTime": {
              "@id": "prov:atTime",
              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
            },
            "entity": {
              "@id": "prov:entity",
              "@type": "@id"
            },
            "hadActivity": {
              "@id": "prov:hadActivity",
              "@type": "@id"
            }
          }
        },
        "qualifiedAssociation": {
          "@id": "prov:qualifiedAssociation",
          "@type": "@id",
          "@context": {
            "agent": {
              "@id": "prov:agent",
              "@type": "@id",
              "@context": {
                "qualifiedDelegation": {
                  "@id": "prov:qualifiedDelegation",
                  "@type": "@id",
                  "@context": {
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "wasInfluencedBy": {
                  "@id": "prov:wasInfluencedBy",
                  "@type": "@id",
                  "@context": {}
                },
                "qualifiedInfluence": {
                  "@id": "prov:qualifiedInfluence",
                  "@type": "@id",
                  "@context": {
                    "influencer": {
                      "@id": "prov:influencer",
                      "@type": "@id",
                      "@context": {}
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    },
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id",
                      "@context": {}
                    }
                  }
                }
              }
            },
            "hadRole": {
              "@id": "prov:hadRole",
              "@type": "@id"
            },
            "hadPlan": {
              "@id": "prov:hadPlan",
              "@type": "@id"
            }
          }
        },
        "wasInfluencedBy": {
          "@id": "prov:wasInfluencedBy",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "qualifiedDelegation": {
              "@id": "prov:qualifiedDelegation",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id",
                  "@context": {
                    "wasAssociatedWith": {
                      "@id": "prov:wasAssociatedWith",
                      "@type": "@id"
                    },
                    "qualifiedAssociation": {
                      "@id": "prov:qualifiedAssociation",
                      "@type": "@id",
                      "@context": {
                        "hadRole": {
                          "@id": "prov:hadRole",
                          "@type": "@id"
                        },
                        "hadPlan": {
                          "@id": "prov:hadPlan",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                }
              }
            },
            "wasAssociatedWith": {
              "@id": "prov:wasAssociatedWith",
              "@type": "@id",
              "@context": {
                "qualifiedDelegation": {
                  "@id": "prov:qualifiedDelegation",
                  "@type": "@id",
                  "@context": {
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "qualifiedAssociation": {
              "@id": "prov:qualifiedAssociation",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id",
                  "@context": {
                    "qualifiedDelegation": {
                      "@id": "prov:qualifiedDelegation",
                      "@type": "@id",
                      "@context": {
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                },
                "hadRole": {
                  "@id": "prov:hadRole",
                  "@type": "@id"
                },
                "hadPlan": {
                  "@id": "prov:hadPlan",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "qualifiedInfluence": {
          "@id": "prov:qualifiedInfluence",
          "@type": "@id",
          "@context": {
            "influencer": {
              "@id": "prov:influencer",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                },
                "qualifiedDelegation": {
                  "@id": "prov:qualifiedDelegation",
                  "@type": "@id",
                  "@context": {
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id",
                      "@context": {
                        "wasAssociatedWith": {
                          "@id": "prov:wasAssociatedWith",
                          "@type": "@id"
                        },
                        "qualifiedAssociation": {
                          "@id": "prov:qualifiedAssociation",
                          "@type": "@id",
                          "@context": {
                            "hadRole": {
                              "@id": "prov:hadRole",
                              "@type": "@id"
                            },
                            "hadPlan": {
                              "@id": "prov:hadPlan",
                              "@type": "@id"
                            }
                          }
                        }
                      }
                    }
                  }
                },
                "wasAssociatedWith": {
                  "@id": "prov:wasAssociatedWith",
                  "@type": "@id",
                  "@context": {
                    "qualifiedDelegation": {
                      "@id": "prov:qualifiedDelegation",
                      "@type": "@id",
                      "@context": {
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                },
                "qualifiedUsage": {
                  "@id": "prov:qualifiedUsage",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    }
                  }
                },
                "qualifiedStart": {
                  "@id": "prov:qualifiedStart",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedEnd": {
                  "@id": "prov:qualifiedEnd",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedAssociation": {
                  "@id": "prov:qualifiedAssociation",
                  "@type": "@id",
                  "@context": {
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id",
                      "@context": {
                        "qualifiedDelegation": {
                          "@id": "prov:qualifiedDelegation",
                          "@type": "@id",
                          "@context": {
                            "agent": {
                              "@id": "prov:agent",
                              "@type": "@id"
                            },
                            "hadActivity": {
                              "@id": "prov:hadActivity",
                              "@type": "@id"
                            }
                          }
                        }
                      }
                    },
                    "hadRole": {
                      "@id": "prov:hadRole",
                      "@type": "@id"
                    },
                    "hadPlan": {
                      "@id": "prov:hadPlan",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "entity": {
              "@id": "prov:entity",
              "@type": "@id"
            },
            "activity": {
              "@id": "prov:activity",
              "@type": "@id",
              "@context": {
                "wasAssociatedWith": {
                  "@id": "prov:wasAssociatedWith",
                  "@type": "@id",
                  "@context": {
                    "actedOnBehalfOf": {
                      "@id": "prov:actedOnBehalfOf",
                      "@type": "@id"
                    },
                    "qualifiedDelegation": {
                      "@id": "prov:qualifiedDelegation",
                      "@type": "@id",
                      "@context": {
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                },
                "qualifiedUsage": {
                  "@id": "prov:qualifiedUsage",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    }
                  }
                },
                "qualifiedStart": {
                  "@id": "prov:qualifiedStart",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedEnd": {
                  "@id": "prov:qualifiedEnd",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedAssociation": {
                  "@id": "prov:qualifiedAssociation",
                  "@type": "@id",
                  "@context": {
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id",
                      "@context": {
                        "qualifiedDelegation": {
                          "@id": "prov:qualifiedDelegation",
                          "@type": "@id",
                          "@context": {
                            "agent": {
                              "@id": "prov:agent",
                              "@type": "@id"
                            },
                            "hadActivity": {
                              "@id": "prov:hadActivity",
                              "@type": "@id"
                            }
                          }
                        }
                      }
                    },
                    "hadRole": {
                      "@id": "prov:hadRole",
                      "@type": "@id"
                    },
                    "hadPlan": {
                      "@id": "prov:hadPlan",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "agent": {
              "@id": "prov:agent",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                },
                "qualifiedDelegation": {
                  "@id": "prov:qualifiedDelegation",
                  "@type": "@id",
                  "@context": {
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id",
                      "@context": {
                        "wasAssociatedWith": {
                          "@id": "prov:wasAssociatedWith",
                          "@type": "@id"
                        },
                        "qualifiedUsage": {
                          "@id": "prov:qualifiedUsage",
                          "@type": "@id",
                          "@context": {
                            "atTime": {
                              "@id": "prov:atTime",
                              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                            }
                          }
                        },
                        "qualifiedStart": {
                          "@id": "prov:qualifiedStart",
                          "@type": "@id",
                          "@context": {
                            "atTime": {
                              "@id": "prov:atTime",
                              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                            },
                            "hadActivity": {
                              "@id": "prov:hadActivity",
                              "@type": "@id"
                            }
                          }
                        },
                        "qualifiedEnd": {
                          "@id": "prov:qualifiedEnd",
                          "@type": "@id",
                          "@context": {
                            "atTime": {
                              "@id": "prov:atTime",
                              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                            },
                            "hadActivity": {
                              "@id": "prov:hadActivity",
                              "@type": "@id"
                            }
                          }
                        },
                        "qualifiedAssociation": {
                          "@id": "prov:qualifiedAssociation",
                          "@type": "@id",
                          "@context": {
                            "hadRole": {
                              "@id": "prov:hadRole",
                              "@type": "@id"
                            },
                            "hadPlan": {
                              "@id": "prov:hadPlan",
                              "@type": "@id"
                            }
                          }
                        }
                      }
                    }
                  }
                }
              }
            }
          }
        },
        "qualifiedDelegation": {
          "@id": "prov:qualifiedDelegation",
          "@type": "@id",
          "@context": {
            "agent": {
              "@id": "prov:agent",
              "@type": "@id"
            },
            "hadActivity": {
              "@id": "prov:hadActivity",
              "@type": "@id",
              "@context": {
                "wasAssociatedWith": {
                  "@id": "prov:wasAssociatedWith",
                  "@type": "@id",
                  "@context": {}
                },
                "qualifiedAssociation": {
                  "@id": "prov:qualifiedAssociation",
                  "@type": "@id",
                  "@context": {
                    "hadRole": {
                      "@id": "prov:hadRole",
                      "@type": "@id"
                    },
                    "hadPlan": {
                      "@id": "prov:hadPlan",
                      "@type": "@id"
                    }
                  }
                },
                "wasInfluencedBy": {
                  "@id": "prov:wasInfluencedBy",
                  "@type": "@id",
                  "@context": {}
                },
                "qualifiedInfluence": {
                  "@id": "prov:qualifiedInfluence",
                  "@type": "@id",
                  "@context": {
                    "influencer": {
                      "@id": "prov:influencer",
                      "@type": "@id",
                      "@context": {}
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    },
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id",
                      "@context": {}
                    }
                  }
                }
              }
            }
          }
        },
        "wasGeneratedBy": {
          "@id": "prov:wasGeneratedBy",
          "@type": "@id",
          "@context": {
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id",
              "@context": {
                "actedOnBehalfOf": {
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                },
                "qualifiedDelegation": {
                  "@id": "prov:qualifiedDelegation",
                  "@type": "@id",
                  "@context": {
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id",
                  "@context": {
                    "actedOnBehalfOf": {
                      "@id": "prov:actedOnBehalfOf",
                      "@type": "@id"
                    },
                    "qualifiedDelegation": {
                      "@id": "prov:qualifiedDelegation",
                      "@type": "@id",
                      "@context": {
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id"
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id",
                  "@context": {
                    "actedOnBehalfOf": {
                      "@id": "prov:actedOnBehalfOf",
                      "@type": "@id"
                    },
                    "qualifiedDelegation": {
                      "@id": "prov:qualifiedDelegation",
                      "@type": "@id",
                      "@context": {
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                }
              }
            }
          }
        },
        "wasAttributedTo": {
          "@id": "prov:wasAttributedTo",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "qualifiedDelegation": {
              "@id": "prov:qualifiedDelegation",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id",
                  "@context": {
                    "wasAssociatedWith": {
                      "@id": "prov:wasAssociatedWith",
                      "@type": "@id"
                    },
                    "qualifiedAssociation": {
                      "@id": "prov:qualifiedAssociation",
                      "@type": "@id",
                      "@context": {
                        "hadRole": {
                          "@id": "prov:hadRole",
                          "@type": "@id"
                        },
                        "hadPlan": {
                          "@id": "prov:hadPlan",
                          "@type": "@id"
                        }
                      }
                    },
                    "wasInfluencedBy": {
                      "@id": "prov:wasInfluencedBy",
                      "@type": "@id"
                    },
                    "qualifiedInfluence": {
                      "@id": "prov:qualifiedInfluence",
                      "@type": "@id",
                      "@context": {
                        "influencer": {
                          "@id": "prov:influencer",
                          "@type": "@id"
                        },
                        "entity": {
                          "@id": "prov:entity",
                          "@type": "@id"
                        },
                        "activity": {
                          "@id": "prov:activity",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                }
              }
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id",
              "@context": {
                "wasAssociatedWith": {
                  "@id": "prov:wasAssociatedWith",
                  "@type": "@id"
                },
                "qualifiedAssociation": {
                  "@id": "prov:qualifiedAssociation",
                  "@type": "@id",
                  "@context": {
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    },
                    "hadRole": {
                      "@id": "prov:hadRole",
                      "@type": "@id"
                    },
                    "hadPlan": {
                      "@id": "prov:hadPlan",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id",
                  "@context": {
                    "wasAssociatedWith": {
                      "@id": "prov:wasAssociatedWith",
                      "@type": "@id"
                    },
                    "qualifiedUsage": {
                      "@id": "prov:qualifiedUsage",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        }
                      }
                    },
                    "qualifiedStart": {
                      "@id": "prov:qualifiedStart",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    },
                    "qualifiedEnd": {
                      "@id": "prov:qualifiedEnd",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    },
                    "qualifiedAssociation": {
                      "@id": "prov:qualifiedAssociation",
                      "@type": "@id",
                      "@context": {
                        "hadRole": {
                          "@id": "prov:hadRole",
                          "@type": "@id"
                        },
                        "hadPlan": {
                          "@id": "prov:hadPlan",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id",
                  "@context": {
                    "wasAssociatedWith": {
                      "@id": "prov:wasAssociatedWith",
                      "@type": "@id"
                    },
                    "qualifiedUsage": {
                      "@id": "prov:qualifiedUsage",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        }
                      }
                    },
                    "qualifiedStart": {
                      "@id": "prov:qualifiedStart",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    },
                    "qualifiedEnd": {
                      "@id": "prov:qualifiedEnd",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    },
                    "qualifiedAssociation": {
                      "@id": "prov:qualifiedAssociation",
                      "@type": "@id",
                      "@context": {
                        "hadRole": {
                          "@id": "prov:hadRole",
                          "@type": "@id"
                        },
                        "hadPlan": {
                          "@id": "prov:hadPlan",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "wasInvalidatedBy": {
          "@id": "prov:wasInvalidatedBy",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "qualifiedDelegation": {
              "@id": "prov:qualifiedDelegation",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id",
                  "@context": {
                    "wasAssociatedWith": {
                      "@id": "prov:wasAssociatedWith",
                      "@type": "@id"
                    },
                    "qualifiedAssociation": {
                      "@id": "prov:qualifiedAssociation",
                      "@type": "@id",
                      "@context": {
                        "hadRole": {
                          "@id": "prov:hadRole",
                          "@type": "@id"
                        },
                        "hadPlan": {
                          "@id": "prov:hadPlan",
                          "@type": "@id"
                        }
                      }
                    },
                    "wasInfluencedBy": {
                      "@id": "prov:wasInfluencedBy",
                      "@type": "@id"
                    },
                    "qualifiedInfluence": {
                      "@id": "prov:qualifiedInfluence",
                      "@type": "@id",
                      "@context": {
                        "influencer": {
                          "@id": "prov:influencer",
                          "@type": "@id"
                        },
                        "entity": {
                          "@id": "prov:entity",
                          "@type": "@id"
                        },
                        "activity": {
                          "@id": "prov:activity",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                }
              }
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id",
              "@context": {
                "wasAssociatedWith": {
                  "@id": "prov:wasAssociatedWith",
                  "@type": "@id"
                },
                "qualifiedAssociation": {
                  "@id": "prov:qualifiedAssociation",
                  "@type": "@id",
                  "@context": {
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    },
                    "hadRole": {
                      "@id": "prov:hadRole",
                      "@type": "@id"
                    },
                    "hadPlan": {
                      "@id": "prov:hadPlan",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id",
                  "@context": {
                    "wasAssociatedWith": {
                      "@id": "prov:wasAssociatedWith",
                      "@type": "@id"
                    },
                    "qualifiedUsage": {
                      "@id": "prov:qualifiedUsage",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        }
                      }
                    },
                    "qualifiedStart": {
                      "@id": "prov:qualifiedStart",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    },
                    "qualifiedEnd": {
                      "@id": "prov:qualifiedEnd",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    },
                    "qualifiedAssociation": {
                      "@id": "prov:qualifiedAssociation",
                      "@type": "@id",
                      "@context": {
                        "hadRole": {
                          "@id": "prov:hadRole",
                          "@type": "@id"
                        },
                        "hadPlan": {
                          "@id": "prov:hadPlan",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id",
                  "@context": {
                    "wasAssociatedWith": {
                      "@id": "prov:wasAssociatedWith",
                      "@type": "@id"
                    },
                    "qualifiedUsage": {
                      "@id": "prov:qualifiedUsage",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        }
                      }
                    },
                    "qualifiedStart": {
                      "@id": "prov:qualifiedStart",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    },
                    "qualifiedEnd": {
                      "@id": "prov:qualifiedEnd",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    },
                    "qualifiedAssociation": {
                      "@id": "prov:qualifiedAssociation",
                      "@type": "@id",
                      "@context": {
                        "hadRole": {
                          "@id": "prov:hadRole",
                          "@type": "@id"
                        },
                        "hadPlan": {
                          "@id": "prov:hadPlan",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "wasQuotedFrom": {
          "@id": "prov:wasQuotedFrom",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "qualifiedDelegation": {
              "@id": "prov:qualifiedDelegation",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id",
                  "@context": {
                    "wasAssociatedWith": {
                      "@id": "prov:wasAssociatedWith",
                      "@type": "@id"
                    },
                    "qualifiedAssociation": {
                      "@id": "prov:qualifiedAssociation",
                      "@type": "@id",
                      "@context": {
                        "hadRole": {
                          "@id": "prov:hadRole",
                          "@type": "@id"
                        },
                        "hadPlan": {
                          "@id": "prov:hadPlan",
                          "@type": "@id"
                        }
                      }
                    },
                    "wasInfluencedBy": {
                      "@id": "prov:wasInfluencedBy",
                      "@type": "@id"
                    },
                    "qualifiedInfluence": {
                      "@id": "prov:qualifiedInfluence",
                      "@type": "@id",
                      "@context": {
                        "influencer": {
                          "@id": "prov:influencer",
                          "@type": "@id"
                        },
                        "entity": {
                          "@id": "prov:entity",
                          "@type": "@id"
                        },
                        "activity": {
                          "@id": "prov:activity",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                }
              }
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id",
              "@context": {
                "wasAssociatedWith": {
                  "@id": "prov:wasAssociatedWith",
                  "@type": "@id"
                },
                "qualifiedAssociation": {
                  "@id": "prov:qualifiedAssociation",
                  "@type": "@id",
                  "@context": {
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    },
                    "hadRole": {
                      "@id": "prov:hadRole",
                      "@type": "@id"
                    },
                    "hadPlan": {
                      "@id": "prov:hadPlan",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id",
                  "@context": {
                    "wasAssociatedWith": {
                      "@id": "prov:wasAssociatedWith",
                      "@type": "@id"
                    },
                    "qualifiedUsage": {
                      "@id": "prov:qualifiedUsage",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        }
                      }
                    },
                    "qualifiedStart": {
                      "@id": "prov:qualifiedStart",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    },
                    "qualifiedEnd": {
                      "@id": "prov:qualifiedEnd",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    },
                    "qualifiedAssociation": {
                      "@id": "prov:qualifiedAssociation",
                      "@type": "@id",
                      "@context": {
                        "hadRole": {
                          "@id": "prov:hadRole",
                          "@type": "@id"
                        },
                        "hadPlan": {
                          "@id": "prov:hadPlan",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id",
                  "@context": {
                    "wasAssociatedWith": {
                      "@id": "prov:wasAssociatedWith",
                      "@type": "@id"
                    },
                    "qualifiedUsage": {
                      "@id": "prov:qualifiedUsage",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        }
                      }
                    },
                    "qualifiedStart": {
                      "@id": "prov:qualifiedStart",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    },
                    "qualifiedEnd": {
                      "@id": "prov:qualifiedEnd",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    },
                    "qualifiedAssociation": {
                      "@id": "prov:qualifiedAssociation",
                      "@type": "@id",
                      "@context": {
                        "hadRole": {
                          "@id": "prov:hadRole",
                          "@type": "@id"
                        },
                        "hadPlan": {
                          "@id": "prov:hadPlan",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "wasRevisionOf": {
          "@id": "prov:wasRevisionOf",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "qualifiedDelegation": {
              "@id": "prov:qualifiedDelegation",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id",
                  "@context": {
                    "wasAssociatedWith": {
                      "@id": "prov:wasAssociatedWith",
                      "@type": "@id"
                    },
                    "qualifiedAssociation": {
                      "@id": "prov:qualifiedAssociation",
                      "@type": "@id",
                      "@context": {
                        "hadRole": {
                          "@id": "prov:hadRole",
                          "@type": "@id"
                        },
                        "hadPlan": {
                          "@id": "prov:hadPlan",
                          "@type": "@id"
                        }
                      }
                    },
                    "wasInfluencedBy": {
                      "@id": "prov:wasInfluencedBy",
                      "@type": "@id"
                    },
                    "qualifiedInfluence": {
                      "@id": "prov:qualifiedInfluence",
                      "@type": "@id",
                      "@context": {
                        "influencer": {
                          "@id": "prov:influencer",
                          "@type": "@id"
                        },
                        "entity": {
                          "@id": "prov:entity",
                          "@type": "@id"
                        },
                        "activity": {
                          "@id": "prov:activity",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                }
              }
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id",
              "@context": {
                "wasAssociatedWith": {
                  "@id": "prov:wasAssociatedWith",
                  "@type": "@id"
                },
                "qualifiedAssociation": {
                  "@id": "prov:qualifiedAssociation",
                  "@type": "@id",
                  "@context": {
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    },
                    "hadRole": {
                      "@id": "prov:hadRole",
                      "@type": "@id"
                    },
                    "hadPlan": {
                      "@id": "prov:hadPlan",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id",
                  "@context": {
                    "wasAssociatedWith": {
                      "@id": "prov:wasAssociatedWith",
                      "@type": "@id"
                    },
                    "qualifiedUsage": {
                      "@id": "prov:qualifiedUsage",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        }
                      }
                    },
                    "qualifiedStart": {
                      "@id": "prov:qualifiedStart",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    },
                    "qualifiedEnd": {
                      "@id": "prov:qualifiedEnd",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    },
                    "qualifiedAssociation": {
                      "@id": "prov:qualifiedAssociation",
                      "@type": "@id",
                      "@context": {
                        "hadRole": {
                          "@id": "prov:hadRole",
                          "@type": "@id"
                        },
                        "hadPlan": {
                          "@id": "prov:hadPlan",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id",
                  "@context": {
                    "wasAssociatedWith": {
                      "@id": "prov:wasAssociatedWith",
                      "@type": "@id"
                    },
                    "qualifiedUsage": {
                      "@id": "prov:qualifiedUsage",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        }
                      }
                    },
                    "qualifiedStart": {
                      "@id": "prov:qualifiedStart",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    },
                    "qualifiedEnd": {
                      "@id": "prov:qualifiedEnd",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    },
                    "qualifiedAssociation": {
                      "@id": "prov:qualifiedAssociation",
                      "@type": "@id",
                      "@context": {
                        "hadRole": {
                          "@id": "prov:hadRole",
                          "@type": "@id"
                        },
                        "hadPlan": {
                          "@id": "prov:hadPlan",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "mentionOf": {
          "@id": "prov:mentionOf",
          "@type": "@id",
          "@context": {
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "qualifiedDelegation": {
              "@id": "prov:qualifiedDelegation",
              "@type": "@id",
              "@context": {
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                },
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id",
                  "@context": {
                    "wasAssociatedWith": {
                      "@id": "prov:wasAssociatedWith",
                      "@type": "@id"
                    },
                    "qualifiedAssociation": {
                      "@id": "prov:qualifiedAssociation",
                      "@type": "@id",
                      "@context": {
                        "hadRole": {
                          "@id": "prov:hadRole",
                          "@type": "@id"
                        },
                        "hadPlan": {
                          "@id": "prov:hadPlan",
                          "@type": "@id"
                        }
                      }
                    },
                    "wasInfluencedBy": {
                      "@id": "prov:wasInfluencedBy",
                      "@type": "@id"
                    },
                    "qualifiedInfluence": {
                      "@id": "prov:qualifiedInfluence",
                      "@type": "@id",
                      "@context": {
                        "influencer": {
                          "@id": "prov:influencer",
                          "@type": "@id"
                        },
                        "entity": {
                          "@id": "prov:entity",
                          "@type": "@id"
                        },
                        "activity": {
                          "@id": "prov:activity",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                }
              }
            },
            "wasInfluencedBy": {
              "@id": "prov:wasInfluencedBy",
              "@type": "@id",
              "@context": {
                "wasAssociatedWith": {
                  "@id": "prov:wasAssociatedWith",
                  "@type": "@id"
                },
                "qualifiedAssociation": {
                  "@id": "prov:qualifiedAssociation",
                  "@type": "@id",
                  "@context": {
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id"
                    },
                    "hadRole": {
                      "@id": "prov:hadRole",
                      "@type": "@id"
                    },
                    "hadPlan": {
                      "@id": "prov:hadPlan",
                      "@type": "@id"
                    }
                  }
                }
              }
            },
            "qualifiedInfluence": {
              "@id": "prov:qualifiedInfluence",
              "@type": "@id",
              "@context": {
                "influencer": {
                  "@id": "prov:influencer",
                  "@type": "@id",
                  "@context": {
                    "wasAssociatedWith": {
                      "@id": "prov:wasAssociatedWith",
                      "@type": "@id"
                    },
                    "qualifiedUsage": {
                      "@id": "prov:qualifiedUsage",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        }
                      }
                    },
                    "qualifiedStart": {
                      "@id": "prov:qualifiedStart",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    },
                    "qualifiedEnd": {
                      "@id": "prov:qualifiedEnd",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    },
                    "qualifiedAssociation": {
                      "@id": "prov:qualifiedAssociation",
                      "@type": "@id",
                      "@context": {
                        "hadRole": {
                          "@id": "prov:hadRole",
                          "@type": "@id"
                        },
                        "hadPlan": {
                          "@id": "prov:hadPlan",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                },
                "entity": {
                  "@id": "prov:entity",
                  "@type": "@id"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id",
                  "@context": {
                    "wasAssociatedWith": {
                      "@id": "prov:wasAssociatedWith",
                      "@type": "@id"
                    },
                    "qualifiedUsage": {
                      "@id": "prov:qualifiedUsage",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        }
                      }
                    },
                    "qualifiedStart": {
                      "@id": "prov:qualifiedStart",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    },
                    "qualifiedEnd": {
                      "@id": "prov:qualifiedEnd",
                      "@type": "@id",
                      "@context": {
                        "atTime": {
                          "@id": "prov:atTime",
                          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    },
                    "qualifiedAssociation": {
                      "@id": "prov:qualifiedAssociation",
                      "@type": "@id",
                      "@context": {
                        "hadRole": {
                          "@id": "prov:hadRole",
                          "@type": "@id"
                        },
                        "hadPlan": {
                          "@id": "prov:hadPlan",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                },
                "agent": {
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              }
            }
          }
        },
        "qualifiedGeneration": {
          "@id": "prov:qualifiedGeneration",
          "@type": "@id",
          "@context": {
            "atTime": {
              "@id": "prov:atTime",
              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
            },
            "activity": {
              "@id": "prov:activity",
              "@type": "@id",
              "@context": {
                "qualifiedUsage": {
                  "@id": "prov:qualifiedUsage",
                  "@type": "@id",
                  "@context": {
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedCommunication": {
                  "@id": "prov:qualifiedCommunication",
                  "@type": "@id",
                  "@context": {
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedStart": {
                  "@id": "prov:qualifiedStart",
                  "@type": "@id",
                  "@context": {
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedEnd": {
                  "@id": "prov:qualifiedEnd",
                  "@type": "@id",
                  "@context": {
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "wasInfluencedBy": {
                  "@id": "prov:wasInfluencedBy",
                  "@type": "@id",
                  "@context": {
                    "actedOnBehalfOf": {
                      "@id": "prov:actedOnBehalfOf",
                      "@type": "@id"
                    },
                    "qualifiedDelegation": {
                      "@id": "prov:qualifiedDelegation",
                      "@type": "@id",
                      "@context": {
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                },
                "qualifiedInfluence": {
                  "@id": "prov:qualifiedInfluence",
                  "@type": "@id",
                  "@context": {
                    "influencer": {
                      "@id": "prov:influencer",
                      "@type": "@id",
                      "@context": {
                        "actedOnBehalfOf": {
                          "@id": "prov:actedOnBehalfOf",
                          "@type": "@id"
                        },
                        "qualifiedDelegation": {
                          "@id": "prov:qualifiedDelegation",
                          "@type": "@id",
                          "@context": {
                            "agent": {
                              "@id": "prov:agent",
                              "@type": "@id"
                            },
                            "hadActivity": {
                              "@id": "prov:hadActivity",
                              "@type": "@id"
                            }
                          }
                        }
                      }
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    },
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id",
                      "@context": {
                        "actedOnBehalfOf": {
                          "@id": "prov:actedOnBehalfOf",
                          "@type": "@id"
                        },
                        "qualifiedDelegation": {
                          "@id": "prov:qualifiedDelegation",
                          "@type": "@id",
                          "@context": {
                            "agent": {
                              "@id": "prov:agent",
                              "@type": "@id"
                            },
                            "hadActivity": {
                              "@id": "prov:hadActivity",
                              "@type": "@id"
                            }
                          }
                        }
                      }
                    }
                  }
                }
              }
            }
          }
        },
        "qualifiedInvalidation": {
          "@id": "prov:qualifiedInvalidation",
          "@type": "@id",
          "@context": {
            "atTime": {
              "@id": "prov:atTime",
              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
            },
            "activity": {
              "@id": "prov:activity",
              "@type": "@id",
              "@context": {
                "qualifiedUsage": {
                  "@id": "prov:qualifiedUsage",
                  "@type": "@id",
                  "@context": {
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedCommunication": {
                  "@id": "prov:qualifiedCommunication",
                  "@type": "@id",
                  "@context": {
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedStart": {
                  "@id": "prov:qualifiedStart",
                  "@type": "@id",
                  "@context": {
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedEnd": {
                  "@id": "prov:qualifiedEnd",
                  "@type": "@id",
                  "@context": {
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "wasInfluencedBy": {
                  "@id": "prov:wasInfluencedBy",
                  "@type": "@id",
                  "@context": {
                    "actedOnBehalfOf": {
                      "@id": "prov:actedOnBehalfOf",
                      "@type": "@id"
                    },
                    "qualifiedDelegation": {
                      "@id": "prov:qualifiedDelegation",
                      "@type": "@id",
                      "@context": {
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                },
                "qualifiedInfluence": {
                  "@id": "prov:qualifiedInfluence",
                  "@type": "@id",
                  "@context": {
                    "influencer": {
                      "@id": "prov:influencer",
                      "@type": "@id",
                      "@context": {
                        "actedOnBehalfOf": {
                          "@id": "prov:actedOnBehalfOf",
                          "@type": "@id"
                        },
                        "qualifiedDelegation": {
                          "@id": "prov:qualifiedDelegation",
                          "@type": "@id",
                          "@context": {
                            "agent": {
                              "@id": "prov:agent",
                              "@type": "@id"
                            },
                            "hadActivity": {
                              "@id": "prov:hadActivity",
                              "@type": "@id"
                            }
                          }
                        }
                      }
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    },
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id",
                      "@context": {
                        "actedOnBehalfOf": {
                          "@id": "prov:actedOnBehalfOf",
                          "@type": "@id"
                        },
                        "qualifiedDelegation": {
                          "@id": "prov:qualifiedDelegation",
                          "@type": "@id",
                          "@context": {
                            "agent": {
                              "@id": "prov:agent",
                              "@type": "@id"
                            },
                            "hadActivity": {
                              "@id": "prov:hadActivity",
                              "@type": "@id"
                            }
                          }
                        }
                      }
                    }
                  }
                }
              }
            }
          }
        },
        "qualifiedDerivation": {
          "@id": "prov:qualifiedDerivation",
          "@type": "@id",
          "@context": {
            "hadGeneration": {
              "@id": "prov:hadGeneration",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                },
                "activity": {
                  "@id": "prov:activity",
                  "@type": "@id",
                  "@context": {
                    "wasAssociatedWith": {
                      "@id": "prov:wasAssociatedWith",
                      "@type": "@id",
                      "@context": {
                        "actedOnBehalfOf": {
                          "@id": "prov:actedOnBehalfOf",
                          "@type": "@id"
                        },
                        "qualifiedDelegation": {
                          "@id": "prov:qualifiedDelegation",
                          "@type": "@id",
                          "@context": {
                            "agent": {
                              "@id": "prov:agent",
                              "@type": "@id"
                            },
                            "hadActivity": {
                              "@id": "prov:hadActivity",
                              "@type": "@id"
                            }
                          }
                        },
                        "wasInfluencedBy": {
                          "@id": "prov:wasInfluencedBy",
                          "@type": "@id"
                        },
                        "qualifiedInfluence": {
                          "@id": "prov:qualifiedInfluence",
                          "@type": "@id",
                          "@context": {
                            "influencer": {
                              "@id": "prov:influencer",
                              "@type": "@id"
                            },
                            "activity": {
                              "@id": "prov:activity",
                              "@type": "@id"
                            },
                            "agent": {
                              "@id": "prov:agent",
                              "@type": "@id"
                            }
                          }
                        }
                      }
                    },
                    "qualifiedUsage": {
                      "@id": "prov:qualifiedUsage",
                      "@type": "@id",
                      "@context": {}
                    },
                    "qualifiedCommunication": {
                      "@id": "prov:qualifiedCommunication",
                      "@type": "@id",
                      "@context": {
                        "activity": {
                          "@id": "prov:activity",
                          "@type": "@id"
                        }
                      }
                    },
                    "qualifiedStart": {
                      "@id": "prov:qualifiedStart",
                      "@type": "@id",
                      "@context": {
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    },
                    "qualifiedEnd": {
                      "@id": "prov:qualifiedEnd",
                      "@type": "@id",
                      "@context": {
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    },
                    "qualifiedAssociation": {
                      "@id": "prov:qualifiedAssociation",
                      "@type": "@id",
                      "@context": {
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id",
                          "@context": {
                            "qualifiedDelegation": {
                              "@id": "prov:qualifiedDelegation",
                              "@type": "@id",
                              "@context": {
                                "agent": {
                                  "@id": "prov:agent",
                                  "@type": "@id"
                                },
                                "hadActivity": {
                                  "@id": "prov:hadActivity",
                                  "@type": "@id"
                                }
                              }
                            },
                            "wasInfluencedBy": {
                              "@id": "prov:wasInfluencedBy",
                              "@type": "@id",
                              "@context": {}
                            },
                            "qualifiedInfluence": {
                              "@id": "prov:qualifiedInfluence",
                              "@type": "@id",
                              "@context": {
                                "influencer": {
                                  "@id": "prov:influencer",
                                  "@type": "@id",
                                  "@context": {}
                                },
                                "activity": {
                                  "@id": "prov:activity",
                                  "@type": "@id"
                                },
                                "agent": {
                                  "@id": "prov:agent",
                                  "@type": "@id",
                                  "@context": {}
                                }
                              }
                            }
                          }
                        },
                        "hadRole": {
                          "@id": "prov:hadRole",
                          "@type": "@id"
                        },
                        "hadPlan": {
                          "@id": "prov:hadPlan",
                          "@type": "@id"
                        }
                      }
                    },
                    "wasInfluencedBy": {
                      "@id": "prov:wasInfluencedBy",
                      "@type": "@id",
                      "@context": {
                        "actedOnBehalfOf": {
                          "@id": "prov:actedOnBehalfOf",
                          "@type": "@id"
                        },
                        "qualifiedDelegation": {
                          "@id": "prov:qualifiedDelegation",
                          "@type": "@id",
                          "@context": {
                            "agent": {
                              "@id": "prov:agent",
                              "@type": "@id"
                            },
                            "hadActivity": {
                              "@id": "prov:hadActivity",
                              "@type": "@id"
                            }
                          }
                        }
                      }
                    },
                    "qualifiedInfluence": {
                      "@id": "prov:qualifiedInfluence",
                      "@type": "@id",
                      "@context": {
                        "influencer": {
                          "@id": "prov:influencer",
                          "@type": "@id",
                          "@context": {
                            "actedOnBehalfOf": {
                              "@id": "prov:actedOnBehalfOf",
                              "@type": "@id"
                            },
                            "qualifiedDelegation": {
                              "@id": "prov:qualifiedDelegation",
                              "@type": "@id",
                              "@context": {
                                "agent": {
                                  "@id": "prov:agent",
                                  "@type": "@id"
                                },
                                "hadActivity": {
                                  "@id": "prov:hadActivity",
                                  "@type": "@id"
                                }
                              }
                            }
                          }
                        },
                        "activity": {
                          "@id": "prov:activity",
                          "@type": "@id"
                        },
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id",
                          "@context": {
                            "actedOnBehalfOf": {
                              "@id": "prov:actedOnBehalfOf",
                              "@type": "@id"
                            },
                            "qualifiedDelegation": {
                              "@id": "prov:qualifiedDelegation",
                              "@type": "@id",
                              "@context": {
                                "agent": {
                                  "@id": "prov:agent",
                                  "@type": "@id"
                                },
                                "hadActivity": {
                                  "@id": "prov:hadActivity",
                                  "@type": "@id"
                                }
                              }
                            }
                          }
                        }
                      }
                    }
                  }
                }
              }
            },
            "hadActivity": {
              "@id": "prov:hadActivity",
              "@type": "@id",
              "@context": {
                "wasAssociatedWith": {
                  "@id": "prov:wasAssociatedWith",
                  "@type": "@id",
                  "@context": {
                    "actedOnBehalfOf": {
                      "@id": "prov:actedOnBehalfOf",
                      "@type": "@id"
                    },
                    "qualifiedDelegation": {
                      "@id": "prov:qualifiedDelegation",
                      "@type": "@id",
                      "@context": {
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    },
                    "wasInfluencedBy": {
                      "@id": "prov:wasInfluencedBy",
                      "@type": "@id"
                    },
                    "qualifiedInfluence": {
                      "@id": "prov:qualifiedInfluence",
                      "@type": "@id",
                      "@context": {
                        "influencer": {
                          "@id": "prov:influencer",
                          "@type": "@id"
                        },
                        "activity": {
                          "@id": "prov:activity",
                          "@type": "@id"
                        },
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                },
                "qualifiedUsage": {
                  "@id": "prov:qualifiedUsage",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    }
                  }
                },
                "qualifiedStart": {
                  "@id": "prov:qualifiedStart",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedEnd": {
                  "@id": "prov:qualifiedEnd",
                  "@type": "@id",
                  "@context": {
                    "atTime": {
                      "@id": "prov:atTime",
                      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                    },
                    "hadActivity": {
                      "@id": "prov:hadActivity",
                      "@type": "@id"
                    }
                  }
                },
                "qualifiedAssociation": {
                  "@id": "prov:qualifiedAssociation",
                  "@type": "@id",
                  "@context": {
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id",
                      "@context": {
                        "qualifiedDelegation": {
                          "@id": "prov:qualifiedDelegation",
                          "@type": "@id",
                          "@context": {
                            "agent": {
                              "@id": "prov:agent",
                              "@type": "@id"
                            },
                            "hadActivity": {
                              "@id": "prov:hadActivity",
                              "@type": "@id"
                            }
                          }
                        },
                        "wasInfluencedBy": {
                          "@id": "prov:wasInfluencedBy",
                          "@type": "@id",
                          "@context": {}
                        },
                        "qualifiedInfluence": {
                          "@id": "prov:qualifiedInfluence",
                          "@type": "@id",
                          "@context": {
                            "influencer": {
                              "@id": "prov:influencer",
                              "@type": "@id",
                              "@context": {}
                            },
                            "activity": {
                              "@id": "prov:activity",
                              "@type": "@id"
                            },
                            "agent": {
                              "@id": "prov:agent",
                              "@type": "@id",
                              "@context": {}
                            }
                          }
                        }
                      }
                    },
                    "hadRole": {
                      "@id": "prov:hadRole",
                      "@type": "@id"
                    },
                    "hadPlan": {
                      "@id": "prov:hadPlan",
                      "@type": "@id"
                    }
                  }
                },
                "wasInfluencedBy": {
                  "@id": "prov:wasInfluencedBy",
                  "@type": "@id",
                  "@context": {
                    "actedOnBehalfOf": {
                      "@id": "prov:actedOnBehalfOf",
                      "@type": "@id"
                    },
                    "qualifiedDelegation": {
                      "@id": "prov:qualifiedDelegation",
                      "@type": "@id",
                      "@context": {
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id"
                        },
                        "hadActivity": {
                          "@id": "prov:hadActivity",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                },
                "qualifiedInfluence": {
                  "@id": "prov:qualifiedInfluence",
                  "@type": "@id",
                  "@context": {
                    "influencer": {
                      "@id": "prov:influencer",
                      "@type": "@id",
                      "@context": {
                        "actedOnBehalfOf": {
                          "@id": "prov:actedOnBehalfOf",
                          "@type": "@id"
                        },
                        "qualifiedDelegation": {
                          "@id": "prov:qualifiedDelegation",
                          "@type": "@id",
                          "@context": {
                            "agent": {
                              "@id": "prov:agent",
                              "@type": "@id"
                            },
                            "hadActivity": {
                              "@id": "prov:hadActivity",
                              "@type": "@id"
                            }
                          }
                        }
                      }
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id"
                    },
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id",
                      "@context": {
                        "actedOnBehalfOf": {
                          "@id": "prov:actedOnBehalfOf",
                          "@type": "@id"
                        },
                        "qualifiedDelegation": {
                          "@id": "prov:qualifiedDelegation",
                          "@type": "@id",
                          "@context": {
                            "agent": {
                              "@id": "prov:agent",
                              "@type": "@id"
                            },
                            "hadActivity": {
                              "@id": "prov:hadActivity",
                              "@type": "@id"
                            }
                          }
                        }
                      }
                    }
                  }
                }
              }
            },
            "hadUsage": {
              "@id": "prov:hadUsage",
              "@type": "@id",
              "@context": {
                "atTime": {
                  "@id": "prov:atTime",
                  "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                }
              }
            },
            "entity": {
              "@id": "prov:entity",
              "@type": "@id"
            }
          }
        },
        "qualifiedAttribution": {
          "@id": "prov:qualifiedAttribution",
          "@type": "@id",
          "@context": {
            "agent": {
              "@id": "prov:agent",
              "@type": "@id",
              "@context": {
                "wasInfluencedBy": {
                  "@id": "prov:wasInfluencedBy",
                  "@type": "@id",
                  "@context": {
                    "wasAssociatedWith": {
                      "@id": "prov:wasAssociatedWith",
                      "@type": "@id",
                      "@context": {}
                    },
                    "qualifiedAssociation": {
                      "@id": "prov:qualifiedAssociation",
                      "@type": "@id",
                      "@context": {
                        "agent": {
                          "@id": "prov:agent",
                          "@type": "@id"
                        },
                        "hadRole": {
                          "@id": "prov:hadRole",
                          "@type": "@id"
                        },
                        "hadPlan": {
                          "@id": "prov:hadPlan",
                          "@type": "@id"
                        }
                      }
                    }
                  }
                },
                "qualifiedInfluence": {
                  "@id": "prov:qualifiedInfluence",
                  "@type": "@id",
                  "@context": {
                    "influencer": {
                      "@id": "prov:influencer",
                      "@type": "@id",
                      "@context": {
                        "wasAssociatedWith": {
                          "@id": "prov:wasAssociatedWith",
                          "@type": "@id",
                          "@context": {}
                        },
                        "qualifiedUsage": {
                          "@id": "prov:qualifiedUsage",
                          "@type": "@id",
                          "@context": {
                            "atTime": {
                              "@id": "prov:atTime",
                              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                            }
                          }
                        },
                        "qualifiedStart": {
                          "@id": "prov:qualifiedStart",
                          "@type": "@id",
                          "@context": {
                            "atTime": {
                              "@id": "prov:atTime",
                              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                            },
                            "hadActivity": {
                              "@id": "prov:hadActivity",
                              "@type": "@id"
                            }
                          }
                        },
                        "qualifiedEnd": {
                          "@id": "prov:qualifiedEnd",
                          "@type": "@id",
                          "@context": {
                            "atTime": {
                              "@id": "prov:atTime",
                              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                            },
                            "hadActivity": {
                              "@id": "prov:hadActivity",
                              "@type": "@id"
                            }
                          }
                        },
                        "qualifiedAssociation": {
                          "@id": "prov:qualifiedAssociation",
                          "@type": "@id",
                          "@context": {
                            "agent": {
                              "@id": "prov:agent",
                              "@type": "@id"
                            },
                            "hadRole": {
                              "@id": "prov:hadRole",
                              "@type": "@id"
                            },
                            "hadPlan": {
                              "@id": "prov:hadPlan",
                              "@type": "@id"
                            }
                          }
                        }
                      }
                    },
                    "entity": {
                      "@id": "prov:entity",
                      "@type": "@id"
                    },
                    "activity": {
                      "@id": "prov:activity",
                      "@type": "@id",
                      "@context": {
                        "wasAssociatedWith": {
                          "@id": "prov:wasAssociatedWith",
                          "@type": "@id",
                          "@context": {}
                        },
                        "qualifiedUsage": {
                          "@id": "prov:qualifiedUsage",
                          "@type": "@id",
                          "@context": {
                            "atTime": {
                              "@id": "prov:atTime",
                              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                            }
                          }
                        },
                        "qualifiedStart": {
                          "@id": "prov:qualifiedStart",
                          "@type": "@id",
                          "@context": {
                            "atTime": {
                              "@id": "prov:atTime",
                              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                            },
                            "hadActivity": {
                              "@id": "prov:hadActivity",
                              "@type": "@id"
                            }
                          }
                        },
                        "qualifiedEnd": {
                          "@id": "prov:qualifiedEnd",
                          "@type": "@id",
                          "@context": {
                            "atTime": {
                              "@id": "prov:atTime",
                              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
                            },
                            "hadActivity": {
                              "@id": "prov:hadActivity",
                              "@type": "@id"
                            }
                          }
                        },
                        "qualifiedAssociation": {
                          "@id": "prov:qualifiedAssociation",
                          "@type": "@id",
                          "@context": {
                            "agent": {
                              "@id": "prov:agent",
                              "@type": "@id"
                            },
                            "hadRole": {
                              "@id": "prov:hadRole",
                              "@type": "@id"
                            },
                            "hadPlan": {
                              "@id": "prov:hadPlan",
                              "@type": "@id"
                            }
                          }
                        }
                      }
                    },
                    "agent": {
                      "@id": "prov:agent",
                      "@type": "@id",
                      "@context": {}
                    }
                  }
                }
              }
            }
          }
        },
        "hadMember": {
          "@id": "prov:hadMember",
          "@type": "@id"
        }
      }
    },
    "Activity": "prov:Activity",
    "ActivityInfluence": "prov:ActivityInfluence",
    "Agent": "prov:Agent",
    "AgentInfluence": "prov:AgentInfluence",
    "Association": "prov:Association",
    "Attribution": "prov:Attribution",
    "Bundle": "prov:Bundle",
    "Collection": "prov:Collection",
    "Communication": "prov:Communication",
    "Delegation": "prov:Delegation",
    "Derivation": "prov:Derivation",
    "EmptyCollection": "prov:EmptyCollection",
    "End": "prov:End",
    "Entity": "prov:Entity",
    "EntityInfluence": "prov:EntityInfluence",
    "Generation": "prov:Generation",
    "Influence": "prov:Influence",
    "InstantaneousEvent": "prov:InstantaneousEvent",
    "Invalidation": "prov:Invalidation",
    "Location": "prov:Location",
    "Organization": "prov:Organization",
    "Person": "prov:Person",
    "Plan": "prov:Plan",
    "PrimarySource": "prov:PrimarySource",
    "Quotation": "prov:Quotation",
    "Revision": "prov:Revision",
    "Role": "prov:Role",
    "SoftwareAgent": "prov:SoftwareAgent",
    "Start": "prov:Start",
    "Usage": "prov:Usage",
    "ServiceDescription": "prov:ServiceDescription",
    "DirectQueryService": "prov:DirectQueryService",
    "Accept": "prov:Accept",
    "Contribute": "prov:Contribute",
    "Contributor": "prov:Contributor",
    "Copyright": "prov:Copyright",
    "Create": "prov:Create",
    "Creator": "prov:Creator",
    "Modify": "prov:Modify",
    "Publish": "prov:Publish",
    "Publisher": "prov:Publisher",
    "Replace": "prov:Replace",
    "RightsAssignment": "prov:RightsAssignment",
    "RightsHolder": "prov:RightsHolder",
    "Submit": "prov:Submit",
    "Dictionary": "prov:Dictionary",
    "EmptyDictionary": "prov:EmptyDictionary",
    "KeyEntityPair": "prov:KeyEntityPair",
    "Insertion": "prov:Insertion",
    "Removal": "prov:Removal",
    "generatedAtTime": {
      "@id": "prov:generatedAtTime",
      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
    },
    "invalidatedAtTime": {
      "@id": "prov:invalidatedAtTime",
      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
    },
    "startedAtTime": {
      "@id": "prov:startedAtTime",
      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
    },
    "value": "prov:value",
    "provenanceUriTemplate": "prov:provenanceUriTemplate",
    "pairKey": {
      "@id": "prov:pairKey",
      "@type": "http://www.w3.org/2000/01/rdf-schema#Literal"
    },
    "removedKey": {
      "@id": "prov:removedKey",
      "@type": "http://www.w3.org/2000/01/rdf-schema#Literal"
    },
    "influenced": {
      "@id": "prov:influenced",
      "@type": "@id"
    },
    "qualifiedPrimarySource": {
      "@id": "prov:qualifiedPrimarySource",
      "@type": "@id"
    },
    "qualifiedQuotation": {
      "@id": "prov:qualifiedQuotation",
      "@type": "@id"
    },
    "qualifiedRevision": {
      "@id": "prov:qualifiedRevision",
      "@type": "@id"
    },
    "has_anchor": {
      "@id": "prov:has_anchor",
      "@type": "@id"
    },
    "has_provenance": {
      "@id": "prov:has_provenance",
      "@type": "@id"
    },
    "has_query_service": {
      "@id": "prov:has_query_service",
      "@type": "@id"
    },
    "describesService": {
      "@id": "prov:describesService",
      "@type": "@id"
    },
    "pingback": {
      "@id": "prov:pingback",
      "@type": "@id"
    },
    "dictionary": {
      "@id": "prov:dictionary",
      "@type": "@id"
    },
    "derivedByInsertionFrom": {
      "@id": "prov:derivedByInsertionFrom",
      "@type": "@id"
    },
    "derivedByRemovalFrom": {
      "@id": "prov:derivedByRemovalFrom",
      "@type": "@id"
    },
    "insertedKeyEntityPair": {
      "@id": "prov:insertedKeyEntityPair",
      "@type": "@id"
    },
    "hadDictionaryMember": {
      "@id": "prov:hadDictionaryMember",
      "@type": "@id"
    },
    "pairEntity": {
      "@id": "prov:pairEntity",
      "@type": "@id"
    },
    "qualifiedInsertion": {
      "@id": "prov:qualifiedInsertion",
      "@type": "@id"
    },
    "qualifiedRemoval": {
      "@id": "prov:qualifiedRemoval",
      "@type": "@id"
    },
    "asInBundle": {
      "@id": "prov:asInBundle",
      "@type": "@id"
    },
    "prov": "http://www.w3.org/ns/prov#",
    "xsd": "http://www.w3.org/2001/XMLSchema#",
    "rdfs": "http://www.w3.org/2000/01/rdf-schema#",
    "rdf": "http://www.w3.org/1999/02/22-rdf-syntax-ns#",
    "owl": "http://www.w3.org/2002/07/owl#",
    "uuid": "urn:uuid:",
    "sha1": "urn:hash::sha1:",
    "wf": "arcp://uuid,1f767ad4-ac52-4623-b5bc-dd9faf2b869f/workflow/packed.cwl#",
    "wf4ever": "http://purl.org/wf4ever/wf4ever#",
    "wfdesc": "http://purl.org/wf4ever/wfdesc#",
    "wfprov": "http://purl.org/wf4ever/wfprov#",
    "cwlprov": "https://w3id.org/cwl/prov#",
    "schemaorg": "http://schema.org/",
    "foaf": "http://xmlns.com/foaf/0.1/",
    "oa": "http://www.w3.org/ns/oa#",
    "dct": "http://purl.org/dc/terms/",
    "@version": 1.1
  }
}
```

> <a target="_blank" href="https://json-ld.org/playground/#json-ld=https%3A%2F%2Fraw.githubusercontent.com%2Fogcincubator%2Fprov-cwl%2Fmaster%2Fbuild%2Fannotated%2Fprov%2Ftemplate%2Fexample-prov-profile%2Fcontext.jsonld">View on JSON-LD Playground</a>

You can find the full JSON-LD context here:
<a href="https://raw.githubusercontent.com/ogcincubator/prov-cwl/master/build/annotated/prov/template/example-prov-profile/context.jsonld" target="_blank">https://raw.githubusercontent.com/ogcincubator/prov-cwl/master/build/annotated/prov/template/example-prov-profile/context.jsonld</a>

# For developers

The source code for this Building Block can be found in the following repository:

* URL: <a href="https://github.com/ogcincubator/prov-cwl" target="_blank">https://github.com/ogcincubator/prov-cwl</a>
* Path:
<code><a href="https://github.com/ogcincubator/prov-cwl/blob/HEAD/_sources/example-prov-profile" target="_blank">_sources/example-prov-profile</a></code>

