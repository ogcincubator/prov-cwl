
# CWL (Prov) (Schema)

`ogc.profiles.prov.cwl.provenance` *v0.1*

Common Workflow Language - profile using PROV JSON schema building block.

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
    "endedAtTime": "2029-01-01T22:05:01Z"
  }
}
```

#### jsonld
```jsonld
{
  "@context": "https://ogcincubator.github.io/prov-cwl/build/annotated/profiles/prov/cwl/provenance/context.jsonld",
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

#### ttl
```ttl
@prefix dct: <http://purl.org/dc/terms/> .
@prefix prov: <http://www.w3.org/ns/prov#> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

<file:///github/workspace/ProvProfile> a <file:///github/workspace/MyEntityType> ;
    rdfs:label "EntityExample" ;
    prov:wasGeneratedBy [ dct:type "Activity" ;
            prov:activity <file:///github/workspace/MyActivity> ;
            prov:endedAtTime "2029-01-01T22:05:01+00:00"^^xsd:dateTime ] .


```


### Profile example
JSON
#### json
```json
{
  "id": "uuid:071d1b5c-1b2b-4995-a6e0-80821af85abd",
  "type": "Feature",
  "provType": "Entity",
  "featureType": [
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
            "type": "Entity",
            "featureType": [
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
                "type": "Entity",
                "featureType": [
                  "Plan",
                  "wfdesc:Workflow"
                ],
                "wfdesc:hasSubProcess": [
                  {
                    "id": "wf:main/rev",
                    "type": "Entity",
                    "featureType": [
                      "Plan",
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
                  "type": "Entity",
                  "featureType": [
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
              "type": "Entity",
              "featureType": [
                "wf4ever:File",
                "wfprov:Artifact"
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
                      "type": "Entity",
                      "featureType": [
                        "wfprov:Artifact",
                        "wf4ever:File"
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
                "type": "Entity",
                "featureType": [
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
    "type": "Entity",
    "featureType": [
      "wfprov:Artifact"
    ]
  },
  "cwlprov:basename": "output.txt",
  "cwlprov:nameext": ".txt",
  "cwlprov:nameroot": "output"
}
```

#### jsonld
```jsonld
{
  "@context": "https://ogcincubator.github.io/prov-cwl/build/annotated/profiles/prov/cwl/provenance/context.jsonld",
  "id": "uuid:071d1b5c-1b2b-4995-a6e0-80821af85abd",
  "type": "Feature",
  "provType": "Entity",
  "featureType": [
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
            "type": "Entity",
            "featureType": [
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
                "type": "Entity",
                "featureType": [
                  "Plan",
                  "wfdesc:Workflow"
                ],
                "wfdesc:hasSubProcess": [
                  {
                    "id": "wf:main/rev",
                    "type": "Entity",
                    "featureType": [
                      "Plan",
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
                  "type": "Entity",
                  "featureType": [
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
              "type": "Entity",
              "featureType": [
                "wf4ever:File",
                "wfprov:Artifact"
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
                      "type": "Entity",
                      "featureType": [
                        "wfprov:Artifact",
                        "wf4ever:File"
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
                "type": "Entity",
                "featureType": [
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
    "type": "Entity",
    "featureType": [
      "wfprov:Artifact"
    ]
  },
  "cwlprov:basename": "output.txt",
  "cwlprov:nameext": ".txt",
  "cwlprov:nameroot": "output"
}
```

#### ttl
```ttl
@prefix cwlprov: <https://w3id.org/cwl/prov#> .
@prefix dct: <http://purl.org/dc/terms/> .
@prefix foaf: <http://xmlns.com/foaf/0.1/> .
@prefix prov: <http://www.w3.org/ns/prov#> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix schemaorg: <http://schema.org/> .
@prefix sha1: <urn:hash::sha1:> .
@prefix uuid: <urn:uuid:> .
@prefix wf: <arcp://uuid,1f767ad4-ac52-4623-b5bc-dd9faf2b869f/workflow/packed.cwl#> .
@prefix wf4ever: <http://purl.org/wf4ever/wf4ever#> .
@prefix wfdesc: <http://purl.org/wf4ever/wfdesc#> .
@prefix wfprov: <http://purl.org/wf4ever/wfprov#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

uuid:071d1b5c-1b2b-4995-a6e0-80821af85abd a wf4ever:File,
        wfprov:Artifact,
        prov:Entity ;
    dct:type "Feature" ;
    prov:qualifiedGeneration [ dct:type "Generation" ;
            prov:activity uuid:1f767ad4-ac52-4623-b5bc-dd9faf2b869f ;
            prov:atTime "2018-10-25T15:46:43.020002"^^xsd:dateTime ;
            prov:hadRole <arcp://uuid,1f767ad4-ac52-4623-b5bc-dd9faf2b869f/workflow/packed.cwl#main/primary/output> ],
        [ dct:type "Generation" ;
            prov:activity uuid:d7e8b17e-2d80-4c42-a797-bc3628f52c44 ;
            prov:atTime "2018-10-25T15:46:38.058365"^^xsd:dateTime ;
            prov:hadRole <arcp://uuid,1f767ad4-ac52-4623-b5bc-dd9faf2b869f/workflow/packed.cwl#main/sorted/output> ] ;
    prov:specializationOf sha1:b9214658cc453331b62c2282b772a5c063dbd284 ;
    cwlprov:basename "output.txt" ;
    cwlprov:nameext ".txt" ;
    cwlprov:nameroot "output" .

wf:main a wfdesc:Workflow,
        prov:Plan ;
    rdfs:label "Prospective provenance" ;
    dct:type "Entity" ;
    wfdesc:hasSubProcess <arcp://uuid,1f767ad4-ac52-4623-b5bc-dd9faf2b869f/workflow/packed.cwl#main/rev>,
        <arcp://uuid,1f767ad4-ac52-4623-b5bc-dd9faf2b869f/workflow/packed.cwl#main/sorted> .

<https://orcid.org/0000-0001-9842-9718> rdfs:label "Stian Soiland-Reyes" ;
    dct:type "Agent",
        "Person",
        "schemaorg:Person" ;
    schemaorg:name "Stian Soiland-Reyes" ;
    foaf:name "Stian Soiland-Reyes" .

sha1:97fe1b50b4582cebc7d853796ebd62e3e163aa3f a wfprov:Artifact ;
    dct:type "Entity" .

sha1:b9214658cc453331b62c2282b772a5c063dbd284 a wfprov:Artifact ;
    dct:type "Entity" .

uuid:4ab5a3fe-e481-4f7f-98c4-af8e5dfccb93 dct:type "Entity" ;
    prov:value true .

uuid:6e84364f-faa9-4a27-aaba-5e4b80d9564b a wf4ever:File,
        wfprov:Artifact ;
    dct:type "Entity" ;
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
    prov:qualifiedAssociation [ dct:type "Association" ] ;
    prov:qualifiedEnd [ dct:type "End" ;
            prov:atTime "2018-10-25T15:46:38.069110"^^xsd:dateTime ;
            prov:hadActivity uuid:1f767ad4-ac52-4623-b5bc-dd9faf2b869f ] ;
    prov:qualifiedStart [ dct:type "Start" ;
            prov:atTime "2018-10-25T15:46:36.975235"^^xsd:dateTime ;
            prov:hadActivity uuid:1f767ad4-ac52-4623-b5bc-dd9faf2b869f ] ;
    prov:qualifiedUsage [ dct:type "Usage" ;
            prov:atTime "2018-10-25T15:46:37.067604"^^xsd:dateTime ;
            prov:entity uuid:feabfc2c-e5eb-49d0-ad5c-c19076482265 ;
            prov:hadRole <arcp://uuid,1f767ad4-ac52-4623-b5bc-dd9faf2b869f/workflow/packed.cwl#main/sorted/input> ],
        [ dct:type "Usage" ;
            prov:atTime "2018-10-25T15:46:37.067864"^^xsd:dateTime ;
            prov:entity uuid:4ab5a3fe-e481-4f7f-98c4-af8e5dfccb93 ;
            prov:hadRole <arcp://uuid,1f767ad4-ac52-4623-b5bc-dd9faf2b869f/workflow/packed.cwl#main/sorted/reverse> ] ;
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
            prov:entity uuid:6e84364f-faa9-4a27-aaba-5e4b80d9564b ;
            prov:hadRole <arcp://uuid,1f767ad4-ac52-4623-b5bc-dd9faf2b869f/workflow/packed.cwl#main/rev/input> ] ;
    prov:wasAssociatedWith uuid:ac9c1653-4291-47bc-86f8-6dedcff13519,
        uuid:f5ce6344-3b3b-4653-84fd-1f5abfa57fb0 .

uuid:fe16801a-7995-4968-a8bb-5e9d46255bb7 a wf4ever:File,
        wfprov:Artifact ;
    dct:type "Entity" ;
    prov:specializationOf sha1:327fc7aedf4f6b69a42a7c8b808dc5a7aff61376 ;
    cwlprov:basename "whale.txt" ;
    cwlprov:nameext ".txt" ;
    cwlprov:nameroot "whale" .

uuid:feabfc2c-e5eb-49d0-ad5c-c19076482265 a wf4ever:File,
        wfprov:Artifact ;
    dct:type "Entity" ;
    prov:qualifiedGeneration [ dct:type "Generation" ;
            prov:activity uuid:f81dd60b-46db-4e58-b9f9-5606de1f10de ;
            prov:atTime "2018-10-25T15:46:36.963254"^^xsd:dateTime ;
            prov:hadRole <arcp://uuid,1f767ad4-ac52-4623-b5bc-dd9faf2b869f/workflow/packed.cwl#main/rev/output> ] ;
    prov:specializationOf sha1:97fe1b50b4582cebc7d853796ebd62e3e163aa3f ;
    cwlprov:basename "output.txt" ;
    cwlprov:nameext ".txt" ;
    cwlprov:nameroot "output" .

<arcp://uuid,1f767ad4-ac52-4623-b5bc-dd9faf2b869f/workflow/packed.cwl#main/rev> a wfdesc:Process,
        prov:Plan ;
    dct:type "Entity" .

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
            prov:entity uuid:fe16801a-7995-4968-a8bb-5e9d46255bb7 ;
            prov:hadRole <arcp://uuid,1f767ad4-ac52-4623-b5bc-dd9faf2b869f/workflow/packed.cwl#main/input> ],
        [ dct:type "Usage" ;
            prov:atTime "2018-10-25T15:46:35.303643"^^xsd:dateTime ;
            prov:entity uuid:ed8d007b-a1f3-4bfe-b390-08df074d712d ;
            prov:hadRole <arcp://uuid,1f767ad4-ac52-4623-b5bc-dd9faf2b869f/workflow/packed.cwl#main/reverse_sort> ] ;
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


### Profile example
JSON
#### json
```json
{
  "id": "uuid:071d1b5c-1b2b-4995-a6e0-80821af85abd",
  "type": "Entity",
  "featureType": [
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
            "type": "Entity",
            "featureType": [
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
                "type": "Entity",
                "featureType": [
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
    "type": "Entity",
    "featureType": [
      "wfprov:Artifact"
    ]
  },
  "cwlprov:basename": "output.txt",
  "cwlprov:nameext": ".txt",
  "cwlprov:nameroot": "output"
}
```

#### jsonld
```jsonld
{
  "@context": "https://ogcincubator.github.io/prov-cwl/build/annotated/profiles/prov/cwl/provenance/context.jsonld",
  "id": "uuid:071d1b5c-1b2b-4995-a6e0-80821af85abd",
  "type": "Entity",
  "featureType": [
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
            "type": "Entity",
            "featureType": [
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
                "type": "Entity",
                "featureType": [
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
    "type": "Entity",
    "featureType": [
      "wfprov:Artifact"
    ]
  },
  "cwlprov:basename": "output.txt",
  "cwlprov:nameext": ".txt",
  "cwlprov:nameroot": "output"
}
```

#### ttl
```ttl
@prefix cwlprov: <https://w3id.org/cwl/prov#> .
@prefix dct: <http://purl.org/dc/terms/> .
@prefix prov: <http://www.w3.org/ns/prov#> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix sha1: <urn:hash::sha1:> .
@prefix uuid: <urn:uuid:> .
@prefix wf: <arcp://uuid,1f767ad4-ac52-4623-b5bc-dd9faf2b869f/workflow/packed.cwl#> .
@prefix wf4ever: <http://purl.org/wf4ever/wf4ever#> .
@prefix wfdesc: <http://purl.org/wf4ever/wfdesc#> .
@prefix wfprov: <http://purl.org/wf4ever/wfprov#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

uuid:071d1b5c-1b2b-4995-a6e0-80821af85abd a wf4ever:File,
        wfprov:Artifact ;
    dct:type "Entity" ;
    prov:qualifiedGeneration [ dct:type "Generation" ;
            prov:activity uuid:1f767ad4-ac52-4623-b5bc-dd9faf2b869f ;
            prov:atTime "2018-10-25T15:46:43.020002"^^xsd:dateTime ;
            prov:hadRole <arcp://uuid,1f767ad4-ac52-4623-b5bc-dd9faf2b869f/workflow/packed.cwl#main/primary/output> ],
        [ dct:type "Generation" ;
            prov:activity uuid:d7e8b17e-2d80-4c42-a797-bc3628f52c44 ;
            prov:atTime "2018-10-25T15:46:38.058365"^^xsd:dateTime ;
            prov:hadRole <arcp://uuid,1f767ad4-ac52-4623-b5bc-dd9faf2b869f/workflow/packed.cwl#main/sorted/output> ] ;
    prov:specializationOf sha1:b9214658cc453331b62c2282b772a5c063dbd284 ;
    cwlprov:basename "output.txt" ;
    cwlprov:nameext ".txt" ;
    cwlprov:nameroot "output" .

wf:main a wfdesc:Workflow,
        prov:Plan ;
    rdfs:label "Prospective provenance" ;
    dct:type "Entity" ;
    wfdesc:hasSubProcess <arcp://uuid,1f767ad4-ac52-4623-b5bc-dd9faf2b869f/workflow/packed.cwl#main/rev>,
        <arcp://uuid,1f767ad4-ac52-4623-b5bc-dd9faf2b869f/workflow/packed.cwl#main/sorted> .

<arcp://uuid,1f767ad4-ac52-4623-b5bc-dd9faf2b869f/workflow/packed.cwl#main/rev> dct:type "Entity",
        "Plan",
        "wfdesc:Process" .

sha1:b9214658cc453331b62c2282b772a5c063dbd284 a wfprov:Artifact ;
    dct:type "Entity" .

uuid:d7e8b17e-2d80-4c42-a797-bc3628f52c44 rdfs:label "Run of workflow/packed.cwl#main/sorted" ;
    dct:type "Activity",
        "wfprov:ProcessRun" ;
    prov:qualifiedAssociation [ dct:type "Association" ] ;
    prov:qualifiedEnd [ dct:type "End" ;
            prov:atTime "2018-10-25T15:46:38.069110"^^xsd:dateTime ;
            prov:hadActivity uuid:1f767ad4-ac52-4623-b5bc-dd9faf2b869f ] .

uuid:1f767ad4-ac52-4623-b5bc-dd9faf2b869f rdfs:label "Run of workflow/packed.cwl#main" ;
    dct:type "Activity",
        "wfprov:WorkflowRun" ;
    prov:qualifiedAssociation [ dct:type "Association" ;
            prov:hadPlan wf:main ] ;
    prov:startedAtTime "2018-10-25T15:46:35.211026"^^xsd:dateTime ;
    prov:wasAssociatedWith uuid:ac9c1653-4291-47bc-86f8-6dedcff13519 .


```

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: CWL Provenance Chain
$ref: https://ogcincubator.github.io/bblock-prov-schema/build/annotated/ogc-utils/prov/schema.yaml
x-jsonld-prefixes:
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

Links to the schema:

* YAML version: [schema.yaml](https://ogcincubator.github.io/prov-cwl/build/annotated/profiles/prov/cwl/provenance/schema.json)
* JSON version: [schema.json](https://ogcincubator.github.io/prov-cwl/build/annotated/profiles/prov/cwl/provenance/schema.yaml)


# JSON-LD Context

```jsonld
{
  "@context": {
    "wasInfluencedBy": {
      "@context": {
        "href": {
          "@type": "@id",
          "@id": "oa:hasTarget"
        },
        "rel": {
          "@context": {
            "@base": "http://www.iana.org/assignments/relation/"
          },
          "@id": "http://www.iana.org/assignments/relation",
          "@type": "@id"
        },
        "anchor": {},
        "hreflang": "dct:language",
        "title": "rdfs:label",
        "length": "dct:extent"
      },
      "@id": "prov:wasInfluencedBy",
      "@type": "@id"
    },
    "qualifiedInfluence": {
      "@context": {
        "influencer": {
          "@context": {
            "href": {
              "@type": "@id",
              "@id": "oa:hasTarget"
            },
            "rel": {
              "@context": {
                "@base": "http://www.iana.org/assignments/relation/"
              },
              "@id": "http://www.iana.org/assignments/relation",
              "@type": "@id"
            },
            "anchor": {},
            "hreflang": "dct:language",
            "title": "rdfs:label",
            "length": "dct:extent"
          },
          "@id": "prov:influencer",
          "@type": "@id"
        },
        "agent": {
          "@context": {
            "href": {
              "@type": "@id",
              "@id": "oa:hasTarget"
            },
            "rel": {
              "@context": {
                "@base": "http://www.iana.org/assignments/relation/"
              },
              "@id": "http://www.iana.org/assignments/relation",
              "@type": "@id"
            },
            "anchor": {},
            "hreflang": "dct:language",
            "title": "rdfs:label",
            "length": "dct:extent"
          },
          "@id": "prov:agent",
          "@type": "@id"
        }
      },
      "@id": "prov:qualifiedInfluence",
      "@type": "@id"
    },
    "provType": "@type",
    "prov:type": {},
    "type": "dct:type",
    "hadMember": {
      "@id": "prov:hadMember",
      "@type": "@id"
    },
    "id": "@id",
    "featureType": "@type",
    "entityType": "@type",
    "has_provenance": {
      "@id": "dct:provenance",
      "@type": "@id"
    },
    "wasGeneratedBy": {
      "@id": "prov:wasGeneratedBy",
      "@type": "@id"
    },
    "wasAttributedTo": {
      "@context": {
        "href": {
          "@type": "@id",
          "@id": "oa:hasTarget"
        },
        "rel": {
          "@context": {
            "@base": "http://www.iana.org/assignments/relation/"
          },
          "@id": "http://www.iana.org/assignments/relation",
          "@type": "@id"
        },
        "anchor": {},
        "hreflang": "dct:language",
        "title": "rdfs:label",
        "length": "dct:extent"
      },
      "@id": "prov:wasAttributedTo",
      "@type": "@id"
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
    "atLocation": {
      "@id": "prov:atLocation",
      "@type": "@id"
    },
    "links": {
      "@context": {
        "href": {
          "@type": "@id",
          "@id": "oa:hasTarget"
        },
        "rel": {
          "@context": {
            "@base": "http://www.iana.org/assignments/relation/"
          },
          "@id": "http://www.iana.org/assignments/relation",
          "@type": "@id"
        },
        "anchor": {},
        "hreflang": "dct:language",
        "title": "rdfs:label",
        "length": "dct:extent"
      },
      "@id": "rdfs:seeAlso"
    },
    "qualifiedGeneration": {
      "@id": "prov:qualifiedGeneration",
      "@type": "@id"
    },
    "qualifiedInvalidation": {
      "@id": "prov:qualifiedInvalidation",
      "@type": "@id"
    },
    "qualifiedDerivation": {
      "@id": "prov:qualifiedDerivation",
      "@type": "@id"
    },
    "qualifiedAttribution": {
      "@id": "prov:qualifiedAttribution",
      "@type": "@id"
    },
    "activityType": "@type",
    "agentType": "@type",
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
    "atTime": {
      "@id": "prov:atTime",
      "@type": "xsd:dateTime"
    },
    "endedAtTime": {
      "@id": "prov:endedAtTime",
      "@type": "xsd:dateTime"
    },
    "generatedAtTime": {
      "@id": "prov:generatedAtTime",
      "@type": "xsd:dateTime"
    },
    "invalidatedAtTime": {
      "@id": "prov:invalidatedAtTime",
      "@type": "xsd:dateTime"
    },
    "startedAtTime": {
      "@id": "prov:startedAtTime",
      "@type": "xsd:dateTime"
    },
    "value": "prov:value",
    "provenanceUriTemplate": "prov:provenanceUriTemplate",
    "pairKey": {
      "@id": "prov:pairKey",
      "@type": "rdfs:Literal"
    },
    "removedKey": {
      "@id": "prov:removedKey",
      "@type": "rdfs:Literal"
    },
    "actedOnBehalfOf": {
      "@id": "prov:actedOnBehalfOf",
      "@type": "@id"
    },
    "agent": {
      "@id": "prov:agent",
      "@type": "@id"
    },
    "entity": {
      "@id": "prov:entity",
      "@type": "@id"
    },
    "generated": {
      "@id": "prov:generated",
      "@type": "@id"
    },
    "hadActivity": {
      "@id": "prov:hadActivity",
      "@type": "@id"
    },
    "activity": {
      "@id": "prov:activity",
      "@type": "@id"
    },
    "hadGeneration": {
      "@id": "prov:hadGeneration",
      "@type": "@id"
    },
    "hadPlan": {
      "@id": "prov:hadPlan",
      "@type": "@id"
    },
    "hadRole": {
      "@id": "prov:hadRole",
      "@type": "@id"
    },
    "hadUsage": {
      "@id": "prov:hadUsage",
      "@type": "@id"
    },
    "influenced": {
      "@id": "prov:influenced",
      "@type": "@id"
    },
    "influencer": {
      "@id": "prov:influencer",
      "@type": "@id"
    },
    "invalidated": {
      "@id": "prov:invalidated",
      "@type": "@id"
    },
    "qualifiedAssociation": {
      "@id": "prov:qualifiedAssociation",
      "@type": "@id"
    },
    "qualifiedCommunication": {
      "@id": "prov:qualifiedCommunication",
      "@type": "@id"
    },
    "qualifiedDelegation": {
      "@id": "prov:qualifiedDelegation",
      "@type": "@id"
    },
    "qualifiedEnd": {
      "@id": "prov:qualifiedEnd",
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
    "qualifiedStart": {
      "@id": "prov:qualifiedStart",
      "@type": "@id"
    },
    "qualifiedUsage": {
      "@id": "prov:qualifiedUsage",
      "@type": "@id"
    },
    "used": {
      "@id": "prov:used",
      "@type": "@id"
    },
    "wasAssociatedWith": {
      "@id": "prov:wasAssociatedWith",
      "@type": "@id",
      "@context": {
        "href": {
          "@type": "@id",
          "@id": "oa:hasTarget"
        },
        "rel": {
          "@context": {
            "@base": "http://www.iana.org/assignments/relation/"
          },
          "@id": "http://www.iana.org/assignments/relation",
          "@type": "@id"
        },
        "anchor": {},
        "hreflang": "dct:language",
        "title": "rdfs:label",
        "length": "dct:extent"
      }
    },
    "wasEndedBy": {
      "@id": "prov:wasEndedBy",
      "@type": "@id"
    },
    "wasInformedBy": {
      "@id": "prov:wasInformedBy",
      "@type": "@id"
    },
    "wasStartedBy": {
      "@id": "prov:wasStartedBy",
      "@type": "@id"
    },
    "has_anchor": {
      "@id": "prov:has_anchor",
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
    "mentionOf": {
      "@id": "prov:mentionOf",
      "@type": "@id"
    },
    "name": "rdfs:label",
    "prov": "http://www.w3.org/ns/prov#",
    "xsd": "http://www.w3.org/2001/XMLSchema#",
    "rdfs": "http://www.w3.org/2000/01/rdf-schema#",
    "dct": "http://purl.org/dc/terms/",
    "rdf": "http://www.w3.org/1999/02/22-rdf-syntax-ns#",
    "oa": "http://www.w3.org/ns/oa#",
    "uuid": "urn:uuid:",
    "sha1": "urn:hash::sha1:",
    "wf": "arcp://uuid,1f767ad4-ac52-4623-b5bc-dd9faf2b869f/workflow/packed.cwl#",
    "wf4ever": "http://purl.org/wf4ever/wf4ever#",
    "wfdesc": "http://purl.org/wf4ever/wfdesc#",
    "wfprov": "http://purl.org/wf4ever/wfprov#",
    "cwlprov": "https://w3id.org/cwl/prov#",
    "schemaorg": "http://schema.org/",
    "foaf": "http://xmlns.com/foaf/0.1/",
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://ogcincubator.github.io/prov-cwl/build/annotated/profiles/prov/cwl/provenance/context.jsonld)


# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/ogcincubator/prov-cwl](https://github.com/ogcincubator/prov-cwl)
* Path: `_sources/provenance`

