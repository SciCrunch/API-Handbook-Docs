# Resource Information Network (RIN) Services

## Introduction

The RIN metadata APIs are provided via an ElasticSearch endpoint.  The metadata is extracted from Community Authorities that provide information about research resourced identified by a Research Resource Identifier (RRID).  The data from these authorities is processed via the FDI Lab's Foundry - a message-oriented, horizontally scalable ETL system for scientific data integration and enhancement (Ozyurt and Grethe 2018).&#x20;

### Research Resource Identifiers (RRIDs)

RRIDs are meant to improve the standards of research resource reporting in order to support rigor and reproducibility. RRID's original concept was envisioned during NIH meetings in 2010-2011. These meetings, which were hosted by NIH’s National Center for Research Resources, involved the development of an initial white paper on resource identification by principal investigators for dkNET (Drs. Maryann Martone and Jeffrey Grethe) and the current lead for the RRID project (Dr. Anita Bandrowski). This white paper was posted in 2012.  [The Research Resource Initiative](https://www.force11.org/node/4145) was then started by Dr. Maryann Martone, through the[ Neuroscience Information Framework](https://neuinfo.org/) (NIF).  Initially, meetings with publishers from 2011-2013 (hosted by NIF, NIH’s NIDA and [the International Neuroinformatics Coordinating Facility (INCF)](https://www.incf.org/) were held to discuss the problem of research resource identification. From the potential solutions discussed in these meetings, a pilot project was born. This project was started in 2014 and led by Drs. Martone and Bandrowski. It was initiated through FORCE11 with leverage, infrastructure, and support from dkNET. Through this framework from dkNET, the initial RRID portal was created. The pilot included additional partners (i.e. the Oregon Health & Science University Library and[ the Monarch Initiative](https://monarchinitiative.org/)). In 2015, the pilot project concluded. A publication describing how RRIDs were being used by authors in 100 papers from 20 journals was released. The publication described how the use of RRIDs was showing potential for benefiting the accurate reproducibility of research in the scientific community. In respect to this potential, RRIDs are currently being used in over 340 journals (August, 2017). The RRID project is supported by leadership of Dr. Anita Bandrowski and works in collaboration with [SciCrunch](https://scicrunch.org/), [NIF](https://neuinfo.org/), and [dkNET](https://dknet.org/).

RRIDs are persistent and unique identifiers for referencing a research resource and are used for promoting research resource identification and tracking. Catalog numbers change, disappear or can be reused for another resource, but RRIDs always resolve to the same research resource and endure beyond the existence of the research resource itself. It’s an easy and practical method for improving reproducibility, transparency and tracking.

Examples of RRIDs:

* Antibody: [Estrogen receptor beta antibody](https://dknet.org/data/record/nif-0000-07730-1/AB\_10618531/resolver), RRID:AB\_10618531
* Cell line: [HK-2 \[Human kidney\]](https://dknet.org/data/record/SCR\_013869-1/CVCL\_0302/resolver), RRID:CVCL\_0302
* Mouse model: [TSOD.C-Nidd6](https://dknet.org/data/record/nlx\_154697-1/IMSR\_CARD:280/resolver), RRID:IMSR\_-CARD:280
* Software: [ANOVA](https://dknet.org/data/record/nlx\_144509-1/SCR\_002427/resolver), RRID:SCR\_002427

### References

Ozyurt, I. B., & Grethe, J. S. (2018). Foundry: a message-oriented, horizontally scalable ETL system for scientific data integration and enhancement. Database : the journal of biological databases and curation, 2018, bay130. [https://doi.org/10.1093/database/bay130](https://doi.org/10.1093/database/bay130)
