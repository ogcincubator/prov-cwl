
# Provenance Profile (Schema)

`cwlprov.provenance` *v0.1*

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
    "endedAtTime": "2029-01-01T22:05:01Z"
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
    "endedAtTime": "2029-01-01T22:05:01Z"
  },
  "@context": "https://ogcincubator.github.io/prov-cwl/build/annotated/provenance/context.jsonld"
}
```

#### ttl
```ttl
@prefix prov: <http://www.w3.org/ns/prov#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

<file:///github/workspace/ProvProfile> prov:wasGeneratedBy [ prov:endedAtTime "2029-01-01T22:05:01+00:00"^^xsd:dateTime ] .


```


### Profile example
JSON
#### json
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

#### jsonld
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
  "@context": "https://ogcincubator.github.io/prov-cwl/build/annotated/provenance/context.jsonld"
}
```

#### ttl
```ttl
@prefix cwlprov: <https://w3id.org/cwl/prov#> .
@prefix prov: <http://www.w3.org/ns/prov#> .
@prefix sha1: <urn:hash::sha1:> .
@prefix uuid: <urn:uuid:> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

uuid:071d1b5c-1b2b-4995-a6e0-80821af85abd prov:qualifiedGeneration [ prov:atTime "2018-10-25T15:46:43.020002"^^xsd:dateTime ],
        [ prov:atTime "2018-10-25T15:46:38.058365"^^xsd:dateTime ] ;
    prov:specializationOf sha1:b9214658cc453331b62c2282b772a5c063dbd284 ;
    cwlprov:basename "output.txt" ;
    cwlprov:nameext ".txt" ;
    cwlprov:nameroot "output" .


```


### Profile example
JSON
#### json
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

#### jsonld
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
  "@context": "https://ogcincubator.github.io/prov-cwl/build/annotated/provenance/context.jsonld"
}
```

#### ttl
```ttl
@prefix cwlprov: <https://w3id.org/cwl/prov#> .
@prefix prov: <http://www.w3.org/ns/prov#> .
@prefix sha1: <urn:hash::sha1:> .
@prefix uuid: <urn:uuid:> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

uuid:071d1b5c-1b2b-4995-a6e0-80821af85abd prov:qualifiedGeneration [ prov:atTime "2018-10-25T15:46:38.058365"^^xsd:dateTime ],
        [ prov:atTime "2018-10-25T15:46:43.020002"^^xsd:dateTime ] ;
    prov:specializationOf sha1:b9214658cc453331b62c2282b772a5c063dbd284 ;
    cwlprov:basename "output.txt" ;
    cwlprov:nameext ".txt" ;
    cwlprov:nameroot "output" .


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

* YAML version: [schema.yaml](https://ogcincubator.github.io/prov-cwl/build/annotated/provenance/schema.json)
* JSON version: [schema.json](https://ogcincubator.github.io/prov-cwl/build/annotated/provenance/schema.yaml)


# JSON-LD Context

```jsonld
{
  "@context": {
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
    "id": "@id",
    "has_provenance": {
      "@context": {
        "name": "rdfs:label",
        "actedOnBehalfOf": {
          "@context": {
            "href": "oa:hasTarget",
            "rel": {
              "@context": {
                "@base": "http://www.iana.org/assignments/relation/"
              },
              "@id": "http://www.iana.org/assignments/relation",
              "@type": "@id"
            },
            "type": "dct:type",
            "hreflang": "dct:language",
            "title": "rdfs:label",
            "length": "dct:extent"
          },
          "@id": "prov:actedOnBehalfOf",
          "@type": "@id"
        },
        "qualifiedDelegation": {
          "@context": {
            "agent": {
              "@id": "prov:agent",
              "@type": "@id"
            },
            "hadActivity": {
              "@id": "prov:hadActivity",
              "@type": "@id"
            }
          },
          "@id": "prov:qualifiedDelegation",
          "@type": "@id"
        }
      },
      "@id": "prov:has_provenance",
      "@type": "@id"
    },
    "wasGeneratedBy": {
      "@context": {},
      "@id": "prov:wasGeneratedBy",
      "@type": "@id"
    },
    "wasAttributedTo": {
      "@context": {
        "name": "rdfs:label",
        "actedOnBehalfOf": {
          "@id": "prov:actedOnBehalfOf",
          "@type": "@id"
        },
        "qualifiedDelegation": {
          "@context": {
            "agent": {
              "@id": "prov:agent",
              "@type": "@id"
            },
            "hadActivity": {
              "@id": "prov:hadActivity",
              "@type": "@id"
            }
          },
          "@id": "prov:qualifiedDelegation",
          "@type": "@id"
        },
        "href": "oa:hasTarget",
        "rel": {
          "@context": {
            "@base": "http://www.iana.org/assignments/relation/"
          },
          "@id": "http://www.iana.org/assignments/relation",
          "@type": "@id"
        },
        "type": "dct:type",
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
      "@context": {
        "name": "rdfs:label",
        "actedOnBehalfOf": {
          "@id": "prov:actedOnBehalfOf",
          "@type": "@id"
        },
        "qualifiedDelegation": {
          "@context": {
            "agent": {
              "@id": "prov:agent",
              "@type": "@id"
            },
            "hadActivity": {
              "@id": "prov:hadActivity",
              "@type": "@id"
            }
          },
          "@id": "prov:qualifiedDelegation",
          "@type": "@id"
        },
        "href": "oa:hasTarget",
        "rel": {
          "@context": {
            "@base": "http://www.iana.org/assignments/relation/"
          },
          "@id": "http://www.iana.org/assignments/relation",
          "@type": "@id"
        },
        "type": "dct:type",
        "hreflang": "dct:language",
        "title": "rdfs:label",
        "length": "dct:extent"
      },
      "@id": "prov:wasInvalidatedBy",
      "@type": "@id"
    },
    "wasQuotedFrom": {
      "@context": {
        "name": "rdfs:label",
        "actedOnBehalfOf": {
          "@id": "prov:actedOnBehalfOf",
          "@type": "@id"
        },
        "qualifiedDelegation": {
          "@context": {
            "agent": {
              "@id": "prov:agent",
              "@type": "@id"
            },
            "hadActivity": {
              "@id": "prov:hadActivity",
              "@type": "@id"
            }
          },
          "@id": "prov:qualifiedDelegation",
          "@type": "@id"
        },
        "href": "oa:hasTarget",
        "rel": {
          "@context": {
            "@base": "http://www.iana.org/assignments/relation/"
          },
          "@id": "http://www.iana.org/assignments/relation",
          "@type": "@id"
        },
        "type": "dct:type",
        "hreflang": "dct:language",
        "title": "rdfs:label",
        "length": "dct:extent"
      },
      "@id": "prov:wasQuotedFrom",
      "@type": "@id"
    },
    "wasRevisionOf": {
      "@context": {
        "name": "rdfs:label",
        "actedOnBehalfOf": {
          "@id": "prov:actedOnBehalfOf",
          "@type": "@id"
        },
        "qualifiedDelegation": {
          "@context": {
            "agent": {
              "@id": "prov:agent",
              "@type": "@id"
            },
            "hadActivity": {
              "@id": "prov:hadActivity",
              "@type": "@id"
            }
          },
          "@id": "prov:qualifiedDelegation",
          "@type": "@id"
        },
        "href": "oa:hasTarget",
        "rel": {
          "@context": {
            "@base": "http://www.iana.org/assignments/relation/"
          },
          "@id": "http://www.iana.org/assignments/relation",
          "@type": "@id"
        },
        "type": "dct:type",
        "hreflang": "dct:language",
        "title": "rdfs:label",
        "length": "dct:extent"
      },
      "@id": "prov:wasRevisionOf",
      "@type": "@id"
    },
    "mentionOf": {
      "@context": {
        "name": "rdfs:label",
        "actedOnBehalfOf": {
          "@id": "prov:actedOnBehalfOf",
          "@type": "@id"
        },
        "qualifiedDelegation": {
          "@context": {
            "agent": {
              "@id": "prov:agent",
              "@type": "@id"
            },
            "hadActivity": {
              "@id": "prov:hadActivity",
              "@type": "@id"
            }
          },
          "@id": "prov:qualifiedDelegation",
          "@type": "@id"
        },
        "href": "oa:hasTarget",
        "rel": {
          "@context": {
            "@base": "http://www.iana.org/assignments/relation/"
          },
          "@id": "http://www.iana.org/assignments/relation",
          "@type": "@id"
        },
        "type": "dct:type",
        "hreflang": "dct:language",
        "title": "rdfs:label",
        "length": "dct:extent"
      },
      "@id": "prov:mentionOf",
      "@type": "@id"
    },
    "atLocation": {
      "@id": "prov:atLocation",
      "@type": "@id"
    },
    "links": {
      "@context": {
        "href": "oa:hasTarget",
        "rel": {
          "@context": {
            "@base": "http://www.iana.org/assignments/relation/"
          },
          "@id": "http://www.iana.org/assignments/relation",
          "@type": "@id"
        },
        "type": "dct:type",
        "hreflang": "dct:language",
        "title": "rdfs:label",
        "length": "dct:extent"
      },
      "@id": "rdfs:seeAlso"
    },
    "qualifiedGeneration": {
      "@context": {
        "atTime": {
          "@id": "prov:atTime",
          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
        },
        "activityType": {
          "@id": "prov:activity",
          "@type": "@id"
        }
      },
      "@id": "prov:qualifiedGeneration",
      "@type": "@id"
    },
    "qualifiedInvalidation": {
      "@context": {
        "atTime": {
          "@id": "prov:atTime",
          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
        },
        "activityType": {
          "@id": "prov:activity",
          "@type": "@id"
        }
      },
      "@id": "prov:qualifiedInvalidation",
      "@type": "@id"
    },
    "qualifiedDerivation": {
      "@context": {
        "hadGeneration": {
          "@context": {
            "atTime": {
              "@id": "prov:atTime",
              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
            },
            "activityType": {
              "@id": "prov:activity",
              "@type": "@id"
            }
          },
          "@id": "prov:hadGeneration",
          "@type": "@id"
        },
        "hadActivity": {
          "@id": "prov:hadActivity",
          "@type": "@id"
        },
        "hadUsage": {
          "@context": {
            "atTime": {
              "@id": "prov:atTime",
              "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
            }
          },
          "@id": "prov:hadUsage",
          "@type": "@id"
        },
        "entity": {
          "@id": "prov:entity",
          "@type": "@id"
        }
      },
      "@id": "prov:qualifiedDerivation",
      "@type": "@id"
    },
    "qualifiedAttribution": {
      "@context": {
        "agent": {
          "@context": {
            "name": "rdfs:label",
            "actedOnBehalfOf": {
              "@context": {
                "href": "oa:hasTarget",
                "rel": {
                  "@context": {
                    "@base": "http://www.iana.org/assignments/relation/"
                  },
                  "@id": "http://www.iana.org/assignments/relation",
                  "@type": "@id"
                },
                "type": "dct:type",
                "hreflang": "dct:language",
                "title": "rdfs:label",
                "length": "dct:extent"
              },
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "qualifiedDelegation": {
              "@context": {
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              },
              "@id": "prov:qualifiedDelegation",
              "@type": "@id"
            }
          },
          "@id": "prov:agent",
          "@type": "@id"
        }
      },
      "@id": "prov:qualifiedAttribution",
      "@type": "@id"
    },
    "endedAtTime": {
      "@id": "prov:endedAtTime",
      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
    },
    "wasAssociatedWith": {
      "@context": {
        "name": "rdfs:label",
        "actedOnBehalfOf": {
          "@id": "prov:actedOnBehalfOf",
          "@type": "@id"
        },
        "qualifiedDelegation": {
          "@context": {
            "agent": {
              "@id": "prov:agent",
              "@type": "@id"
            },
            "hadActivity": {
              "@id": "prov:hadActivity",
              "@type": "@id"
            }
          },
          "@id": "prov:qualifiedDelegation",
          "@type": "@id"
        },
        "href": "oa:hasTarget",
        "rel": {
          "@context": {
            "@base": "http://www.iana.org/assignments/relation/"
          },
          "@id": "http://www.iana.org/assignments/relation",
          "@type": "@id"
        },
        "type": "dct:type",
        "hreflang": "dct:language",
        "title": "rdfs:label",
        "length": "dct:extent"
      },
      "@id": "prov:wasAssociatedWith",
      "@type": "@id"
    },
    "wasInformedBy": {
      "@id": "prov:wasInformedBy",
      "@type": "@id"
    },
    "used": {
      "@context": {},
      "@id": "prov:used",
      "@type": "@id"
    },
    "wasStartedBy": {
      "@context": {},
      "@id": "prov:wasStartedBy",
      "@type": "@id"
    },
    "wasEndedBy": {
      "@context": {},
      "@id": "prov:wasEndedBy",
      "@type": "@id"
    },
    "invalidated": {
      "@context": {},
      "@id": "prov:invalidated",
      "@type": "@id"
    },
    "generated": {
      "@context": {},
      "@id": "prov:generated",
      "@type": "@id"
    },
    "qualifiedUsage": {
      "@context": {
        "atTime": {
          "@id": "prov:atTime",
          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
        },
        "entity": {
          "@id": "prov:entity",
          "@type": "@id"
        }
      },
      "@id": "prov:qualifiedUsage",
      "@type": "@id"
    },
    "qualifiedCommunication": {
      "@context": {
        "activityType": {
          "@id": "prov:activity",
          "@type": "@id"
        },
        "atTime": {
          "@id": "prov:atTime",
          "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
        }
      },
      "@id": "prov:qualifiedCommunication",
      "@type": "@id"
    },
    "qualifiedStart": {
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
      },
      "@id": "prov:qualifiedStart",
      "@type": "@id"
    },
    "qualifiedEnd": {
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
      },
      "@id": "prov:qualifiedEnd",
      "@type": "@id"
    },
    "qualifiedAssociation": {
      "@context": {
        "agent": {
          "@context": {
            "name": "rdfs:label",
            "actedOnBehalfOf": {
              "@context": {
                "href": "oa:hasTarget",
                "rel": {
                  "@context": {
                    "@base": "http://www.iana.org/assignments/relation/"
                  },
                  "@id": "http://www.iana.org/assignments/relation",
                  "@type": "@id"
                },
                "type": "dct:type",
                "hreflang": "dct:language",
                "title": "rdfs:label",
                "length": "dct:extent"
              },
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "qualifiedDelegation": {
              "@context": {
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              },
              "@id": "prov:qualifiedDelegation",
              "@type": "@id"
            }
          },
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
      },
      "@id": "prov:qualifiedAssociation",
      "@type": "@id"
    },
    "hadMember": {
      "@context": {},
      "@id": "prov:hadMember",
      "@type": "@id"
    },
    "wasInfluencedBy": {
      "@context": {
        "name": "rdfs:label",
        "actedOnBehalfOf": {
          "@id": "prov:actedOnBehalfOf",
          "@type": "@id"
        },
        "qualifiedDelegation": {
          "@context": {
            "agent": {
              "@id": "prov:agent",
              "@type": "@id"
            },
            "hadActivity": {
              "@id": "prov:hadActivity",
              "@type": "@id"
            }
          },
          "@id": "prov:qualifiedDelegation",
          "@type": "@id"
        },
        "href": "oa:hasTarget",
        "rel": {
          "@context": {
            "@base": "http://www.iana.org/assignments/relation/"
          },
          "@id": "http://www.iana.org/assignments/relation",
          "@type": "@id"
        },
        "type": "dct:type",
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
            "name": "rdfs:label",
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "qualifiedDelegation": {
              "@context": {
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              },
              "@id": "prov:qualifiedDelegation",
              "@type": "@id"
            },
            "href": "oa:hasTarget",
            "rel": {
              "@context": {
                "@base": "http://www.iana.org/assignments/relation/"
              },
              "@id": "http://www.iana.org/assignments/relation",
              "@type": "@id"
            },
            "type": "dct:type",
            "hreflang": "dct:language",
            "title": "rdfs:label",
            "length": "dct:extent"
          },
          "@id": "prov:influencer",
          "@type": "@id"
        },
        "entity": {
          "@id": "prov:entity",
          "@type": "@id"
        },
        "activityType": {
          "@id": "prov:activity",
          "@type": "@id"
        },
        "agent": {
          "@context": {
            "name": "rdfs:label",
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            },
            "qualifiedDelegation": {
              "@context": {
                "hadActivity": {
                  "@id": "prov:hadActivity",
                  "@type": "@id"
                }
              },
              "@id": "prov:qualifiedDelegation",
              "@type": "@id"
            },
            "href": "oa:hasTarget",
            "rel": {
              "@context": {
                "@base": "http://www.iana.org/assignments/relation/"
              },
              "@id": "http://www.iana.org/assignments/relation",
              "@type": "@id"
            },
            "type": "dct:type",
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
    "uuid": "urn:uuid:",
    "sha1": "urn:hash::sha1:",
    "wf": "arcp://uuid,1f767ad4-ac52-4623-b5bc-dd9faf2b869f/workflow/packed.cwl#",
    "wf4ever": "http://purl.org/wf4ever/wf4ever#",
    "wfdesc": "http://purl.org/wf4ever/wfdesc#",
    "wfprov": "http://purl.org/wf4ever/wfprov#",
    "cwlprov": "https://w3id.org/cwl/prov#",
    "schemaorg": "http://schema.org/",
    "foaf": "http://xmlns.com/foaf/0.1/",
    "prov": "http://www.w3.org/ns/prov#",
    "xsd": "http://www.w3.org/2001/XMLSchema#",
    "rdfs": "http://www.w3.org/2000/01/rdf-schema#",
    "rdf": "http://www.w3.org/1999/02/22-rdf-syntax-ns#",
    "oa": "http://www.w3.org/ns/oa#",
    "dct": "http://purl.org/dc/terms/",
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://ogcincubator.github.io/prov-cwl/build/annotated/provenance/context.jsonld)


# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/ogcincubator/prov-cwl](https://github.com/ogcincubator/prov-cwl)
* Path: `_sources/provenance`

