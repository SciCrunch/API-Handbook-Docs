# RIN Elaticsearch JSON Data Model

Below we provide an example of a returned search result from the RIN services.  The following CURL command can be used to test the service and view the response. The result only shows the first&#x20;

```bash
curl --location 'https://api.scicrunch.io/elastic/v1/RIN_Tool_pr/_search?q=SPM' \
--header 'apikey: <<YOUR API KEY>>'
```

```json
{
    "took": 8,
    "timed_out": false,
    "_shards": {
        "total": 2,
        "successful": 2,
        "skipped": 0,
        "failed": 0
    },
    "hits": {
        "total": 85,
        "max_score": 12.210579,
        "hits": [
            {
                "_index": "scr_005400-registry_resources_pr-rin-2022apr21",
                "_type": "rin",
                "_id": "rrid:scr_007037",
                "_score": 12.210579,
                "_source": {
                    "item": {
                        "supercategory": [
                            {
                                "name": "Resource",
                                "type": "supercategory"
                            }
                        ],
                        "contentTypes": [
                            {
                                "curie": "ilx:0381348",
                                "name": "product"
                            }
                        ],
                        "language": "en",
                        "description": "Software package for analysis of brain imaging data sequences. Sequences can be a series of images from different cohorts, or time-series from same subject. Current release is designed for analysis of fMRI, PET, SPECT, EEG and MEG.",
                        "identifier": "SCR_007037",
                        "docid": "rrid:scr_007037",
                        "uuid": "c136e372-d264-5603-9eb6-6dba1ef16a39",
                        "synonyms": [
                            {
                                "name": "Statistical Parametric Mapping"
                            },
                            {
                                "name": "Statistical Parametric Mapping Software"
                            },
                            {
                                "name": "SPM"
                            },
                            {
                                "name": "SPM12"
                            },
                            {
                                "name": "SPM8"
                            },
                            {
                                "name": "SPM5"
                            },
                            {
                                "name": "SPM2"
                            },
                            {
                                "name": "SPM99"
                            },
                            {
                                "name": "SPM96"
                            }
                        ],
                        "types": [
                            {
                                "name": "image analysis software",
                                "type": "category"
                            },
                            {
                                "name": "time-series analysis software",
                                "type": "category"
                            },
                            {
                                "name": "data processing software",
                                "type": "category"
                            },
                            {
                                "name": "narrative resource",
                                "type": "category"
                            },
                            {
                                "name": "3d time-series analysis software",
                                "type": "category"
                            },
                            {
                                "name": "license",
                                "type": "category"
                            },
                            {
                                "name": "data or information resource",
                                "type": "category"
                            },
                            {
                                "name": "software application",
                                "type": "category"
                            },
                            {
                                "name": "open-source license",
                                "type": "category"
                            },
                            {
                                "name": "gnu general public license",
                                "type": "category"
                            },
                            {
                                "name": "software resource",
                                "type": "category"
                            },
                            {
                                "name": "mri 3d image",
                                "type": "category"
                            },
                            {
                                "name": "3d spatial image",
                                "type": "category"
                            },
                            {
                                "name": "data analysis software",
                                "type": "category"
                            },
                            {
                                "name": "image",
                                "type": "category"
                            }
                        ],
                        "keywords": [
                            {
                                "keyword": "analysis"
                            },
                            {
                                "keyword": "brain"
                            },
                            {
                                "keyword": "imaging"
                            },
                            {
                                "keyword": "data"
                            },
                            {
                                "keyword": "sequence"
                            },
                            {
                                "keyword": "fMRI"
                            },
                            {
                                "keyword": "PET"
                            },
                            {
                                "keyword": "SPECT"
                            },
                            {
                                "keyword": "EEG"
                            },
                            {
                                "keyword": "MEG"
                            },
                            {
                                "keyword": "bio.tools"
                            }
                        ],
                        "curie": "SCR_007037",
                        "availability": [
                            {
                                "description": "Free, Available for download, Freely available",
                                "keyword": "Free, Available for download, Freely available"
                            }
                        ],
                        "alternateIdentifiers": [
                            {
                                "identifier": "nif-0000-00343"
                            },
                            {
                                "identifier": "biotools:SPM"
                            }
                        ],
                        "abbreviations": [
                            {
                                "name": "SPM"
                            }
                        ],
                        "name": "SPM"
                    },
                    "authority": {
                        "name": "SciCrunch Registry"
                    },
                    "distributions": {
                        "current": [
                            {
                                "type": "landing page",
                                "uri": "https://www.fil.ion.ucl.ac.uk/spm/"
                            }
                        ],
                        "deprecated": [
                            {
                                "uri": ""
                            }
                        ],
                        "alternate": [
                            {
                                "uri": "https://github.com/spm"
                            },
                            {
                                "uri": "https://bio.tools/SPM"
                            }
                        ]
                    },
                    "rrid": {
                        "is_unique": "true",
                        "curie": "RRID:SCR_007037",
                        "properCitation": "SPM (RRID:SCR_007037)"
                    },
                    "disco": {
                        "v_uuid": "c136e372-d264-5603-9eb6-6dba1ef16a39"
                    },
                    "graph": {
                        "parent": [
                            {
                                "resource": {
                                    "identifier": "SCR_011603",
                                    "name": "University College London; London; United Kingdom"
                                },
                                "relationship": {
                                    "identifier": "7",
                                    "name": "has_parent_organization"
                                }
                            }
                        ],
                        "related": [
                            {
                                "resource": {
                                    "identifier": "SCR_002613",
                                    "name": "WFU Biological Parametric Mapping Toolbox"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_002619",
                                    "name": "vis: SPM Visualized Statistics toolbox"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_002915",
                                    "name": "LEAD-DBS"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_003276",
                                    "name": "CCHMC Pediatric Brain Templates"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_003772",
                                    "name": "IBMA toolbox"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_005990",
                                    "name": "ArtRepair for robust fMRI"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_005997",
                                    "name": "ASL data processing tool box"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_007354",
                                    "name": "BrainVISA / Anatomist"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_008264",
                                    "name": "MRIcro Software"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_008642",
                                    "name": "xjView: A Viewing Program For SPM"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_009537",
                                    "name": "BrainMagix SPM Viewer"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_009605",
                                    "name": "MarsBaR region of interest toolbox for SPM"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_009630",
                                    "name": "NIRS-SPM"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_009644",
                                    "name": "SPM SS - fMRI functional localizers"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_009652",
                                    "name": "Wisconsin White Matter Hyperintensities Segmentation Toolbox"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_010465",
                                    "name": "Dementia-specific FDG PET Template for SPM analyses"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_013273",
                                    "name": "SPM Anatomy Toolbox"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_007371",
                                    "name": "MIPAV: Medical Image Processing and Visualization"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_001622",
                                    "name": "MATLAB"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_017682",
                                    "name": "hMRI-toolbox"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_019279",
                                    "name": "Sandwich Estimator Toolbox"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            }
                        ],
                        "relationships": [
                            {
                                "resource": {
                                    "identifier": "SCR_013667",
                                    "name": "Neuroimaging Data Model"
                                },
                                "relationship": {
                                    "identifier": "2",
                                    "name": "uses"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_000868",
                                    "name": "imcalc: SPM batch image calculator"
                                },
                                "relationship": {
                                    "identifier": "2",
                                    "name": "uses"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_016591",
                                    "name": "rsfMRI_fconn calculation"
                                },
                                "relationship": {
                                    "identifier": "2",
                                    "name": "is_used_by"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_003560",
                                    "name": "Automatic Analysis"
                                },
                                "relationship": {
                                    "identifier": "2",
                                    "name": "is_used_by"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_018308",
                                    "name": "auto_acpc_reorient"
                                },
                                "relationship": {
                                    "identifier": "2",
                                    "name": "is_used_by"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_003430",
                                    "name": "NeuroImaging Tools and Resources Collaboratory (NITRC)"
                                },
                                "relationship": {
                                    "identifier": "4",
                                    "name": "is_listed_by"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_001377",
                                    "name": "3DVC"
                                },
                                "relationship": {
                                    "identifier": "4",
                                    "name": "is_listed_by"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_006638",
                                    "name": "Debian"
                                },
                                "relationship": {
                                    "identifier": "4",
                                    "name": "is_listed_by"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_014695",
                                    "name": "bio.tools"
                                },
                                "relationship": {
                                    "identifier": "4",
                                    "name": "is_listed_by"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_024411",
                                    "name": "SoftCite"
                                },
                                "relationship": {
                                    "identifier": "4",
                                    "name": "is_listed_by"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_014096",
                                    "name": "Clinical Toolbox for SPM"
                                },
                                "relationship": {
                                    "identifier": "5",
                                    "name": "is_affiliated_with"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_002092",
                                    "name": "Statistical non-Parametric Mapping"
                                },
                                "relationship": {
                                    "identifier": "5",
                                    "name": "is_affiliated_with"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_002613",
                                    "name": "WFU Biological Parametric Mapping Toolbox"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_002619",
                                    "name": "vis: SPM Visualized Statistics toolbox"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_002915",
                                    "name": "LEAD-DBS"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_003276",
                                    "name": "CCHMC Pediatric Brain Templates"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_003772",
                                    "name": "IBMA toolbox"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_005990",
                                    "name": "ArtRepair for robust fMRI"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_005997",
                                    "name": "ASL data processing tool box"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_007354",
                                    "name": "BrainVISA / Anatomist"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_008264",
                                    "name": "MRIcro Software"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_008642",
                                    "name": "xjView: A Viewing Program For SPM"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_009537",
                                    "name": "BrainMagix SPM Viewer"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_009605",
                                    "name": "MarsBaR region of interest toolbox for SPM"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_009630",
                                    "name": "NIRS-SPM"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_009644",
                                    "name": "SPM SS - fMRI functional localizers"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_009652",
                                    "name": "Wisconsin White Matter Hyperintensities Segmentation Toolbox"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_010465",
                                    "name": "Dementia-specific FDG PET Template for SPM analyses"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_013273",
                                    "name": "SPM Anatomy Toolbox"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_007371",
                                    "name": "MIPAV: Medical Image Processing and Visualization"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_001622",
                                    "name": "MATLAB"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_017682",
                                    "name": "hMRI-toolbox"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_019279",
                                    "name": "Sandwich Estimator Toolbox"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_011603",
                                    "name": "University College London; London; United Kingdom"
                                },
                                "relationship": {
                                    "identifier": "7",
                                    "name": "has_parent_organization"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_015956",
                                    "name": "MRTool"
                                },
                                "relationship": {
                                    "identifier": "8",
                                    "name": "is_required_by"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_016656",
                                    "name": "TSDiffAna"
                                },
                                "relationship": {
                                    "identifier": "10",
                                    "name": "provides"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_015890",
                                    "name": "ICN_Atlas"
                                },
                                "relationship": {
                                    "identifier": "11",
                                    "name": "has_plug_in"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_015525",
                                    "name": "UManitoba - JHU Functionally Defined Human White Matter Atlas"
                                },
                                "relationship": {
                                    "identifier": "12",
                                    "name": "works_with"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_015523",
                                    "name": "NIAG Addiction Data"
                                },
                                "relationship": {
                                    "identifier": "12",
                                    "name": "works_with"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_015890",
                                    "name": "ICN_Atlas"
                                },
                                "relationship": {
                                    "identifier": "12",
                                    "name": "works_with"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_017281",
                                    "name": "spm_auto_reorient_coregister"
                                },
                                "relationship": {
                                    "identifier": "12",
                                    "name": "works_with"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_019184",
                                    "name": "Computational Anatomy Toolbox for SPM"
                                },
                                "relationship": {
                                    "identifier": "12",
                                    "name": "works_with"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_004849",
                                    "name": "FieldTrip"
                                },
                                "relationship": {
                                    "identifier": "12",
                                    "name": "works_with"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_010469",
                                    "name": "POAS4SPM"
                                },
                                "relationship": {
                                    "identifier": "12",
                                    "name": "works_with"
                                }
                            }
                        ]
                    },
                    "diseases": {
                        "related": [
                            {
                                "role": "Related Disease",
                                "name": ""
                            }
                        ]
                    },
                    "supportingAwards": [
                        {
                            "agency": {
                                "name": ""
                            }
                        }
                    ],
                    "references": [
                        {
                            "curie": ""
                        }
                    ],
                    "organisms": {
                        "related": [
                            {
                                "role": "Related Species",
                                "species": {
                                    "name": ""
                                }
                            }
                        ]
                    },
                    "dataItem": {
                        "dataTypes": [
                            "item",
                            "authority",
                            "distributions",
                            "rrid",
                            "disco",
                            "graph",
                            "diseases",
                            "supportingAwards",
                            "references",
                            "organisms"
                        ]
                    },
                    "provenance": {
                        "ingestMethod": "dkNET",
                        "ingestTarget": "",
                        "filePattern": "",
                        "ingestTime": "20240205T050425+0000",
                        "creationDate": [
                            "20220129T080239+0000"
                        ],
                        "docId": "626c3a019473880b77dc0164",
                        "primaryKey": "SCR_007037",
                        "lastSeenDate": "20240205T050056+0000"
                    },
                    "mentions": [
                        {
                            "totalResourceMentions": {
                                "count": 7415
                            },
                            "availability": {
                                "keyword": "available"
                            },
                            "totalRRIDMentions": {
                                "count": 311
                            },
                            "totalMentions": {
                                "count": 7508
                            },
                            "timestamp": "2024-02-05 05:04:52.352"
                        }
                    ],
                    "organization": {
                        "hierarchy": {}
                    },
                    "recordValid": true
                }
            },

```
