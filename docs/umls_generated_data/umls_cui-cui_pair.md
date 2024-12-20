# CUI-CUI Data Documentation

---

## Comprehensive CUI-CUI Pair

```plaintext
File Name:         COMPREHENSIVE_CUI_CUI_PAIRS_UMLS2021AB.csv
Maintainer:        Vidul Panickan
Date of Creation:  April 6 2024
Source:            MRREL Table, UMLS 2021AB
License:           UMLS License is required to use this file
```

This dataset provides relationships between Medical Concepts (CUIs) in the Unified Medical Language System (UMLS). Specifically, the table shows the relationship from CUI2 to CUI1. The data is derived from the MRREL table of UMLS 2021AB and has been filtered to include only non-obsolete relationships.

---

#### Example Rows from the Dataset

| **CUI1** | **REL** | **CUI2** | **RELA**               | **SAB** | **SUPPRESS** |
| -------- | ------- | -------- | ---------------------- | ------- | ------------ |
| C0000039 | SY      | C0000039 | translation_of         | MSHSWE  | N            |
| C5550933 | RO      | C5550919 | mechanism_of_action_of | MED-RT  | N            |
| C5550935 | RB      | C1140142 | has_version            | MSH     | N            |

#### How To Read This Table

Each row in the table represents a relationship between two CUIs (Concept Unique Identifiers). For example, the last row can be read as:

- Concept **C1140142** (CUI2) has a **RB** (broader relationship) with **C5550935** (CUI1), more specifically C1140142 **has_version** C5550935. The information comes from the source **MeSH** vocabulary, and the entry is not suppressed (**N**).

---

#### Column Definitions

1. **CUI1**: The Concept Unique Identifier representing the primary medical concept.

   - Example: `C0004096` represents the medical condition "Asthma."

2. **REL**: Defines the type of relationship between CUI2 and CUI1.

   | **Code** | **Description**                                                                                                                                   |
   | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
   | **RB**   | **Has a broader relationship**: CUI2 is broader than CUI1.                                                                                        |
   | **SY**   | **Source asserted synonymy**: Indicates that CUI2 is a synonym of CUI1.                                                                           |
   | **AQ**   | **Allowed qualifier**: Indicates a qualifier that can be applied to CUI2 relative to CUI1.                                                        |
   | **PAR**  | **Has parent relationship**: CUI2 is a parent of CUI1 in the source vocabulary hierarchy.                                                         |
   | **RN**   | **Has a narrower relationship**: CUI2 is narrower than CUI1.                                                                                      |
   | **RO**   | **Has relationship other than synonymous, narrower, or broader**: General relationships outside the categories of synonymy, broader, or narrower. |
   | **CHD**  | **Has child relationship**: CUI2 is a child of CUI1 in the source vocabulary hierarchy.                                                           |
   | **RQ**   | **Related and possibly synonymous**: Indicates that the concepts are related and might be synonyms.                                               |
   | **RL**   | **Relationship is similar or alike**: CUI2 is similar or "alike" to CUI1.                                                                         |
   | **QB**   | **Can be qualified by**: Indicates that CUI2 can qualify CUI1.                                                                                    |

3. **CUI2**:The Concept Unique Identifier representing the secondary concept linked to CUI1 through the relationship.

4. **RELA**: The relationship attribute provides information on the specific relationship.

   - Example: `mechanism_of_action_of`
   - Note: This column may contain missing values (`NaN`)

   **Top 10 Most Frequent RELA Relationships**

   | **Rank** | **Relationship (RELA)** | **Count** |
   | -------- | ----------------------- | --------- |
   | **1**    | inverse_isa             | 2,658,504 |
   | **2**    | isa                     | 2,658,504 |
   | **3**    | has_translation         | 1,754,108 |
   | **4**    | translation_of          | 1,754,108 |
   | **5**    | inactive_ingredient_of  | 1,556,157 |
   | **6**    | has_inactive_ingredient | 1,556,157 |
   | **7**    | has_member              | 1,214,573 |
   | **8**    | member_of               | 1,214,573 |
   | **9**    | classified_as           | 1,183,612 |
   | **10**   | classifies              | 1,183,612 |

5. **SAB**: Source abbreviation indicating the vocabulary or source of the relationship.

   - Example: `MSH` (Medical Subject Headings).

   **Key vocabularies include**:

   - Medical Subject Headings (MSH) and its localized versions (e.g., MSHFRE, MSHSWE).
   - International Classification of Diseases (ICD10, ICD10CM, etc.).
   - Drug Terminologies: RxNorm, MED-RT, ATC.
   - Clinical and Nursing Classifications: CCC, NANDA-I, NIC.
   - Ontologies: Gene Ontology (GO), Human Phenotype Ontology (HPO).
   - Regulatory Terminologies: NCI Thesaurus, CPT, DSM-5.

6. **SUPPRESS**: A flag indicating whether a relationship is suppressed.
   - Values: `N` (Not suppressed).

---

#### Summary Statistics

| **Column**   | **Count**  | **Unique** | **Top**  | **Freq**   |
| ------------ | ---------- | ---------- | -------- | ---------- |
| **CUI1**     | 46,748,144 | 4,505,653  | C0043047 | 90,351     |
| **REL**      | 46,748,144 | 10         | RO       | 18,765,222 |
| **CUI2**     | 46,748,144 | 4,505,653  | C0043047 | 90,351     |
| **RELA**     | 33,552,932 | 966        | isa      | 2,658,504  |
| **SAB**      | 46,748,144 | 117        | MTHSPL   | 4,472,408  |
| **SUPPRESS** | 46,748,144 | 1          | N        | 46,748,144 |

---

#### Notes

1.  **Comprehensive Relationships**: This dataset provides a detailed mapping of medical concepts and their relationships, useful for knowledge graph creation or ontology building.
2.  **Source Variety**: Relationships are sourced from 117 vocabularies, including MSH, MED-RT, and MTHSPL.
3.  **Incomplete RELA**: The RELA column contains missing values for some relationships, requiring careful handling during analysis.

## Other CUI-CUI Pair

---

## CUI-CUI Pair by Suqi

**Suqi** has manually curated CUI-CUI mappings and relationships for the [RENKI](https://arxiv.org/pdf/2410.07454) project. His mappings classify the `R` column (relationship) into three categories of interest from `REL` and `RELA` column in UMLS:

### Categories of Relationships

1. **REL (Logical Relationships)**:

   - Includes relationships:
     - `associated_morphology_of`
     - `pathological_process_of`
     - `is_interpreted_by`
     - `due_to`
     - `definitional_manifestation_of`
     - `occurs_after`
     - `has_causative_agent`
     - `may_be_treated_by`
     - `may_be_prevented_by`

2. **BRD (Narrower to Broader)**:

   - Includes relationships:
     - `active_ingredient_of`
     - `precise_active_ingredient_of`
     - `inverse_isa`
     - `mapped_from`

3. **SIM (Similarity Relationships)**:
   - Includes relationships:
     - `same_as`
     - `was_a`
     - `mth_has_xml_form`
     - `mth_has_plain_text_form`
     - `refers_to`
     - `has_alternative`
     - `is_modification_of`
     - `possibly_equivalent_to`
     - `replaced_by`

Each row in the file contains:

- **X, Y**: The CUIs (Concept Unique Identifiers) forming the relationship.
- **R**: The relationship type grouped into the categories above.

### Example Row

| **X**    | **Y**    | **R** |
| -------- | -------- | ----- |
| C0000039 | C0216971 | SIM   |

#### Interpretation:

- **X** (`C0000039`): Represents the first concept in the relationship.
- **Y** (`C0216971`): Represents the second concept in the relationship.
- **R** (`SIM`): Indicates a **Similarity Relationship**, meaning the two CUIs are considered similar or equivalent in some context (e.g., synonyms or highly related concepts).

Mapping files are available [here](/docs/mapping_files/mapping_overview#mapping-files-by-suqi).

---

## CUI-CUI Pair by Ziming
