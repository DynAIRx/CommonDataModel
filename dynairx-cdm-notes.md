The DynAIRx Common Data Model (CDM) is based on an agreed star schema of a minimium essential data items to support the analysis and visualisation of the clinical data (primarily sourced from England GP practices). The purpose of this is to create a common data language between work packages. 

 This has been mapped to the OMOP CDM to ensure future capabilty to map and re-use based on OMOP data stores, but the OMOP CDM has been simplified to just the basic requirements. Where something needs to be re-added, the OMOP CDM should be consulted first to understand how the two CDMs can be made increasingly interoperable in the future. It should also be noted that the intention is for DynAIRx to run on live EHR or NHS Shared Record systems which do not support OMOP directly. 

Note: Some aspects of OMOP don't map to UK definitions well at the moment, eg. ethnicity, while others are irrelevant, e.g. billing. SnomedCT and DM+D are also UK-specific vocabularies that are being used within DynAIRx, rather than the US or international / WHO versions, and so there have been a number of changes to de-normalise the OMOP CDM to make easier for initial analytics. **This reduces some of the extensibility of DynAIRx CDM when compared to OMOP but will make initial mapping, sharing and use simpler for this project phase.** Once the data dictionaries / codelists have been completed we need to revisit this question as to whether it is worth re-introducing the extensibility at cost of ease of use

List of changes:
Mapping from common NHS terms to OMOP for the initial star schema:
* Demographics -> PERSON
* Encounters -> VISTS, VISIT_DETAIL
* Diagnoses -> CONDITION_OCCURENCE
* Medications -> DRUG_EXPOSURE
* Measurements -> MEASUREMENTS

Added `SEX` and changed `ETHNICITY` to `PERSON` for UK data mapping purposes. 

Abbreviated `CONDITION_OCCURANCE.CONCEPT_ID` to store `SNOMED_ID` rather than having linkage table to vocabulary. 

Removed a lot of the vocabularies and linkages that are hospital specific, especially relating to visits, which are not well described in UK datasets. 

The full [OMOP CDM](OMOP_CDMv5.4_ER_Diagram.mmd) is also included and more information can be foundn at the [OMOP official site](https://ohdsi.github.io/CommonDataModel/)

Discussion and initial design is in [Miro](https://miro.com/app/board/uXjVMZqYnjQ=/)