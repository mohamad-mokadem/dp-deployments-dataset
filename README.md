# Disclosure in Real-World Differential Privacy Deployments: Dataset and Registry Entries

This repository contains the dataset and the draft registry entries for the paper
*Disclosure in Real-World Differential Privacy Deployments: A Checked Dataset and Comparison with the Public Registry*
by Mohamad Mokadem (Northeastern University), written for CY7790: Special Topics in Security and Privacy.

The paper measures how much real-world differential privacy (DP) deployments disclose about themselves,
using the three tiers of the public [DP Deployments Registry](https://registry.opendp.org/deployments-registry/).

## Start here

- **To browse the dataset:** open [`data/deployments.csv`](data/deployments.csv). GitHub shows it as a table with one row per deployment.
- **To understand the columns:** open [`data/column-guide.md`](data/column-guide.md).
- **To read the draft registry entries:** open [`registry-entries.md`](registry-entries.md).

## Files

| File | What it contains |
|---|---|
| [`data/deployments.csv`](data/deployments.csv) | **The main dataset:** 78 DP deployments, one per row |
| [`data/dp-deployments-dataset.xlsx`](data/dp-deployments-dataset.xlsx) | The full dataset as an Excel workbook (download to open). Besides the main sheet, it has a summary, the column guide, the sources, the 10 government agencies where no public DP deployment was found, and the registry entries that were checked but left out, with the reasons |
| [`data/column-guide.md`](data/column-guide.md) | What each column of the dataset means |
| [`registry-entries.md`](registry-entries.md) | **Draft entries for 15 deployments** that are not yet in the registry but already disclose enough for Tier 2 or Tier 3 |

## The dataset in brief

- **78 deployments:** 49 from tech companies, 20 from government agencies and 9 from non-profits.
- **One rule for every value:** a value is recorded only if the organization's own documents state it. Values that only appear in other sources are kept in the Notes column, with where they came from.
- **Tiers:** 36 deployments reach Tier 3, 9 reach Tier 2 and 33 stay at Tier 1. Tier 2 needs all four details: privacy parameters, privacy unit, type of DP and deployment model. Tier 3 also needs a precise privacy unit, how privacy loss adds up, the mechanism and the reasons for the settings, all found in the organization's own sources.
- **Registry comparison:** 38 deployments appear in the registry or its prototype, and 40 appear in neither. 15 of those 40 already disclose enough for Tier 2 or Tier 3.
- **Gaps:** for every deployment, the Gaps column records the important information its sources leave out.
- **Sources:** every row of the dataset has its own Source and Link columns.

The paper's Appendix describes every step of how the dataset was built.

## About the registry entries

Each entry in `registry-entries.md` follows the sections of the registry's schema and lists its sources.
Fields the dataset does not record are marked as still to be filled.
These entries have not been submitted to the registry or reviewed by its editors.
