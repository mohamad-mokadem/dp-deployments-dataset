# Registry entries for 15 deployments not yet in the DP Deployments Registry

These are draft entries for the 15 deployments in the dataset that are in neither the [DP Deployments Registry](https://registry.opendp.org/deployments-registry/) nor its prototype, but already disclose enough for a Tier 2 or Tier 3 entry. They accompany the paper *Disclosure in Real-World Differential Privacy Deployments: A Checked Dataset and Comparison with the Public Registry* (Mohamad Mokadem, Northeastern University).

## How these entries were prepared

- Every value comes from the organization's own documents, listed under **Sources** in each entry. Values that only appear in other sources are not used.
- Each entry follows the sections of the registry's schema (NIST IR 8588, Table 1): basic information, DP variant, privacy loss, deployment model, and, for Tier 3 entries, the deeper details on the privacy unit, accounting, implementation and reasons.
- The tier is my own rating, using the registry's three tiers.
- Some schema fields are not recorded in the dataset, such as intended use, region and access type. These are listed in each entry as **still to be filled** and must be completed from the sources before an entry is submitted.
- These entries have **not** been submitted to the registry or reviewed by its editors.

## Summary

| ID | Organization | Deployment | Tier |
|---|---|---|---|
| [D08](#d08) | Apple | QuickType new-word suggestions | 3 |
| [D15](#d15) | Google | Environmental Insights Explorer | 3 |
| [D17](#d17) | Google | Gboard new-word discovery | 3 |
| [D18](#d18) | Google | Gboard next-word prediction | 3 |
| [D20](#d20) | Google | Google Shopping page-view counts | 3 |
| [D21](#d21) | Google | Google Trends query selection | 3 |
| [D28](#d28) | Google | VaultGemma 1B | 3 |
| [D34](#d34) | LinkedIn (Microsoft) | Race and ethnicity estimation (bias testing) | 3 |
| [D61](#d61) | U.S. Census Bureau | OnTheMap | 3 |
| [D69](#d69) | Wikimedia Foundation | Wikipedia editor statistics (monthly) | 3 |
| [D70](#d70) | Wikimedia Foundation | Wikipedia editor statistics (weekly) | 3 |
| [D65](#d65) | Microsoft with IOM | Global Victim-Perpetrator Synthetic Dataset | 2 |
| [D68](#d68) | Wikimedia Foundation | Russian editor information (one-off release) | 2 |
| [D76](#d76) | UK Office for National Statistics | Differentially private synthetic linked 2011 Census and mortality data (Integrated Data Service) | 2 |
| [D78](#d78) | Meta | Movement Distribution Maps | 2 |

---

## D08

### Apple: QuickType new-word suggestions

**My tier rating:** Tier 3

#### Basic information (Tier 1)

- **Name:** QuickType new-word suggestions
- **Data curator:** Apple
- **Type of data curator:** Tech company
- **Publication year:** 2016
- **Still to be filled:** intended use; data product type; region; sector

#### DP variant and privacy loss (Tier 2)

- **DP variant:** Pure
- **Privacy unit:** One donation (two donations per day)
- **Privacy parameters:** ε = 8
- **Deployment model:** Local

#### Tier 3 details

Same Apple sources as QuickType: event-level unit with a daily limit, per-use-case budget, CMS/HCMS algorithms, reasons for choosing the budget. The registry rates its Emoji entry (same sources) Tier 3. Sources: Apple, Learning with Privacy at Scale; Apple DP overview.

- **Still to be filled:** data domain; unprotected quantities; trust assumptions; release type and its details; data source (static or dynamic); access type; post-processing

#### Evidence from the organization's own documents

Apple overview, exact words: 'For QuickType, Apple uses a privacy budget with epsilon of 8, and submits two donations per day.' Other sources: an archived 2022 copy of the same Apple overview says QuickType used 'a privacy budget with epsilon of 4' with two donations per day, so two versions of the same document give different values, and it is unclear which is newer; Desfontaines converts to ε = 16 per user per day. Apple's 2017 paper says each record is privatized with ε-local differential privacy (type: pure). Tang et al. (arXiv 1709.02753) found on macOS 10.12 that the budget renews every day, so total loss can keep growing

#### Gaps

No total budget over time: Apple gives ε per donation and a daily limit, but not how long the budget lasts or whether it resets. Two versions of Apple's overview give different ε for QuickType (4 and 8), with no explanation

#### Sources

- Apple Differential Privacy Overview; Apple, Learning with Privacy at Scale (2017)
- Link: <https://www.apple.com/privacy/docs/Differential_Privacy_Overview.pdf>

---

## D15

### Google: Environmental Insights Explorer

**My tier rating:** Tier 3

#### Basic information (Tier 1)

- **Name:** Environmental Insights Explorer
- **Data curator:** Google
- **Type of data curator:** Tech company
- **Publication year:** 2024
- **Still to be filled:** intended use; data product type; region; sector

#### DP variant and privacy loss (Tier 2)

- **DP variant:** Pure
- **Privacy unit:** One user, one week
- **Privacy parameters:** ε ≈ 2 (Google's wording: 'ϵ≈2')
- **Deployment model:** Central

#### Tier 3 details

Regions, 9 activity types and 3 trip directions, with trip counts, distance and duration (domain). User-week addition, with other units considered (unit). Clipping, descaling and thresholding of noisy results (post-processing). Laplace noise with activity and metric scaling after secure aggregation (mechanism). Utility-first choice to meet a 3% error target (reasons). Source: Bian et al., arXiv 2407.03496.

- **Still to be filled:** data domain; unprotected quantities; trust assumptions; release type and its details; data source (static or dynamic); access type; post-processing

#### Evidence from the organization's own documents

Google paper (2024), exact words: 'we can achieve a DP guarantee of ϵ≈2 for a privacy unit of (user, week)', using the Laplace mechanism after on-device clipping and secure aggregation; 'actively being used to collect data in production for EIE'. Google's later Mayfly paper describes the same deployment as 'a per-device, per-week DP ε = 2'. Desfontaines also reads it as pure ε-DP

#### Gaps

No total budget across weeks. Google's two papers state the unit differently (user-week and device-week). Data is released yearly, but no total ε across the weeks of a year is given; ε is given only as approximately 2

#### Sources

- arXiv 2407.03496
- Link: <https://arxiv.org/abs/2407.03496>

---

## D17

### Google: Gboard new-word discovery

**My tier rating:** Tier 3

#### Basic information (Tier 1)

- **Name:** Gboard new-word discovery
- **Data curator:** Google
- **Type of data curator:** Tech company
- **Publication year:** 2024
- **Still to be filled:** intended use; data product type; region; sector

#### DP variant and privacy loss (Tier 2)

- **DP variant:** Approximate (ε, δ)
- **Privacy unit:** One word, with at most 60 words per user in 60 days
- **Privacy parameters:** ε = 0.315, δ = 1 × 10^-10
- **Deployment model:** Distributed

#### Tier 3 details

Open vocabulary (domain). Local DP per word; central guarantee per word with at most 60 words in 60 days (unit). Amplification by aggregation (accounting). LDP-TrieHH with subset selection and secure aggregation (mechanism). Reasons for the design. Sources: Sun et al., arXiv 2404.11607; Google blog.

- **Still to be filled:** data domain; unprotected quantities; trust assumptions; release type and its details; data source (static or dynamic); access type; post-processing

#### Evidence from the organization's own documents

Google blog (April 2024), exact words: LDP-TrieHH offers a central DP guarantee of (ε = 0.315, δ = 1e-10) per word with each user contributing at most 60 words in 60 days. Paper: local ε = 10 on each device, for en-US. Other sources: Desfontaines agrees (ε = 0.32 rounded)

#### Gaps

Values given for U.S. English only; other languages not stated. The guarantee is per word; Google gives no total for a user across the up to 60 words they contribute. Applies to en-US and Indonesian; other languages use trusted hardware instead

#### Sources

- Google Research blog
- Link: <https://research.google/blog/improving-gboard-language-models-via-private-federated-analytics/>

---

## D18

### Google: Gboard next-word prediction

**My tier rating:** Tier 3

#### Basic information (Tier 1)

- **Name:** Gboard next-word prediction
- **Data curator:** Google
- **Type of data curator:** Tech company
- **Publication year:** 2022
- **Still to be filled:** intended use; data product type; region; sector

#### DP variant and privacy loss (Tier 2)

- **DP variant:** Approximate (ε, δ)
- **Privacy unit:** One user (each device)
- **Privacy parameters:** ε between 0.994 and 13.69 across the 30+ Gboard models, δ = 1 × 10^-10
- **Deployment model:** Federated + DP

#### Tier 3 details

User-level (device) unit, one participation per 24 hours. rho comes from noise, bounded participation and number of rounds (accounting). DP-FTRL with adaptive clipping (mechanism). Reasons for user-level over example-level. Public pretraining data (unprotected). Sources: Xu et al., arXiv 2305.18465; Google blog.

- **Still to be filled:** data domain; unprotected quantities; trust assumptions; release type and its details; data source (static or dynamic); access type; post-processing

#### Evidence from the organization's own documents

Google Research blog (Feb 2024), exact words: the 30+ Gboard models 'satisfy (ɛ, δ)-DP guarantees of small δ of 10-10 and ɛ between 0.994 and 13.69', and this is 'the largest known deployment of user-level DP in production'. The dataset records the largest ε. Google's 'Private Federated Learning in Gboard' paper defines user-level DP as protecting 'all the training examples from any one particular Gboard user'. Other sources: Desfontaines lists ε up to 10.61 at δ = 10⁻⁵, converted from ρ

#### Gaps

Only a range across 30+ models (ε 0.994 to 13.69); values per model shown only in a chart

#### Sources

- Google Research blog (Feb 2024); Xu et al., arXiv 2305.18465
- Link: <https://research.google/blog/advances-in-private-training-for-production-on-device-language-models/>

---

## D20

### Google: Google Shopping page-view counts

**My tier rating:** Tier 3

#### Basic information (Tier 1)

- **Name:** Google Shopping page-view counts
- **Data curator:** Google
- **Type of data curator:** Tech company
- **Publication year:** 2023
- **Still to be filled:** intended use; data product type; region; sector

#### DP variant and privacy loss (Tier 2)

- **DP variant:** Approximate (ε, δ)
- **Privacy unit:** One user, one day
- **Privacy parameters:** ε = 1, δ = 1 × 10^-9
- **Deployment model:** Central

#### Tier 3 details

Stream of (key, value, time, user) (domain). User-level DP, one event per user per day (unit). Continual release and composition handled with tree aggregation (accounting). Private key selection and binary tree aggregation (mechanism). Reasons: event-level not enough; contribution-bounding trade-off. Source: Zhang et al., arXiv 2303.18086.

- **Still to be filled:** data domain; unprotected quantities; trust assumptions; release type and its details; data source (static or dynamic); access type; post-processing

#### Evidence from the organization's own documents

DP-SQLP paper (Google, VLDB 2024), exact words: 'Each user is bound to contribute one event per day to ensure user level DP guarantee, per day. We use ε=1 for streaming aggregation. For streaming key selection, when choosing ε=1, the equivalent threshold is around 120; when choosing ε=3 ... around 43; and when choosing ε=10 ... around 16. The overall δ=10⁻⁹.' Other sources: none found that disagree

#### Gaps

The ε used for key selection is not stated: the paper lists three options (1, 3 and 10) without saying which was chosen, so the total ε is unknown. Triggering times are not protected (the paper says so)

#### Sources

- DP-SQLP paper, arXiv 2303.18086
- Link: <https://arxiv.org/abs/2303.18086>

---

## D21

### Google: Google Trends query selection

**My tier rating:** Tier 3

#### Basic information (Tier 1)

- **Name:** Google Trends query selection
- **Data curator:** Google
- **Type of data curator:** Tech company
- **Publication year:** 2023
- **Still to be filled:** intended use; data product type; region; sector

#### DP variant and privacy loss (Tier 2)

- **DP variant:** Approximate (ε, δ)
- **Privacy unit:** One user, one query
- **Privacy parameters:** ε = 2, δ = 1 × 10^-10
- **Deployment model:** Central

#### Tier 3 details

Same paper as Google Shopping (its Google Trends section). Source: Zhang et al., arXiv 2303.18086.

- **Still to be filled:** data domain; unprotected quantities; trust assumptions; release type and its details; data source (static or dynamic); access type; post-processing

#### Evidence from the organization's own documents

DP-SQLP paper, exact words: 'We use ε=2 and δ=10⁻¹⁰ for a user-query level DP guarantee, i.e. each query has a budget ε=2 and δ=10⁻¹⁰.' Each user adds at most one event per query, and only queries with at least 50 unique users are considered. Other sources: Desfontaines agrees

#### Gaps

No total budget across all queries one user searches; the guarantee is per query. Protection is per user and query, not per user overall. A deterministic pre-threshold of 50 unique users is applied before DP. Triggering times are not protected

#### Sources

- DP-SQLP paper, arXiv 2303.18086
- Link: <https://arxiv.org/abs/2303.18086>

---

## D28

### Google: VaultGemma 1B

**My tier rating:** Tier 3

#### Basic information (Tier 1)

- **Name:** VaultGemma 1B
- **Data curator:** Google
- **Type of data curator:** Tech company
- **Publication year:** 2025
- **Still to be filled:** intended use; data product type; region; sector

#### DP variant and privacy loss (Tier 2)

- **DP variant:** Approximate (ε, δ)
- **Privacy unit:** One 1,024-token sequence (not one user)
- **Privacy parameters:** ε ≤ 2.0, δ ≤ 1.1 × 10^-10 (upper bounds, as Google states them)
- **Deployment model:** Central (DP training)

#### Tier 3 details

1,024-token sequences; repeated sequences count separately (unit). Accounting for DP-SGD with Poisson sampling. DP-SGD with Gaussian noise (mechanism). Reasons for sequence-level unit and Poisson sampling. Data filtered before DP (unprotected). Sources: VaultGemma report, arXiv 2510.15001; Google blog.

- **Still to be filled:** data domain; unprotected quantities; trust assumptions; release type and its details; data source (static or dynamic); access type; post-processing

#### Evidence from the organization's own documents

VaultGemma report, exact words: 'VaultGemma was trained with a (ε ≤ 2.0, δ ≤ 1.1e-10)-sequence-level DP guarantee, where sequence consists of 1024 tokens after sampling and packing'; repeated sequences count as separate privacy units. Other sources: none found that disagree

#### Gaps

No user-level guarantee: one person can appear in many sequences. Google says packing can split one document across several sequences, so one long document gets weaker protection than one sequence. The guarantee is not per person

#### Sources

- Google Research blog; arXiv 2510.15001
- Link: <https://research.google/blog/vaultgemma-the-worlds-most-capable-differentially-private-llm>

---

## D34

### LinkedIn (Microsoft): Race and ethnicity estimation (bias testing)

**My tier rating:** Tier 3

#### Basic information (Tier 1)

- **Name:** Race and ethnicity estimation (bias testing)
- **Data curator:** LinkedIn (Microsoft)
- **Type of data curator:** Tech company
- **Publication year:** 2024
- **Still to be filled:** intended use; data product type; region; sector

#### DP variant and privacy loss (Tier 2)

- **DP variant:** Pure
- **Privacy unit:** One member's Self-ID survey record
- **Privacy parameters:** ε = 4.5
- **Deployment model:** Local (randomized response on each record)

#### Tier 3 details

Six race and ethnicity categories as a one-hot vector (domain). Each Self-ID record (unit). Probabilistic clipping and secure two-party computation after DP (post-processing). Randomized response (mechanism). Design history explaining why other options were dropped (reasons). Source: Badrinarayanan et al., arXiv 2409.04652.

- **Still to be filled:** data domain; unprotected quantities; trust assumptions; release type and its details; data source (static or dynamic); access type; post-processing

#### Evidence from the organization's own documents

LinkedIn paper, exact words: 'For local DP, we set ε = 4.5, which leads to a flipping rate = 5.26%'; randomized response is applied to each Self-ID record before BISG estimates and secure two-party computation. Other sources: Desfontaines lists ε = 4.5 per user

#### Gaps

No total budget across repeated fairness measurements; LinkedIn relies on a governance process instead. Only Self-ID survey answers get local DP; the surname-and-location (BISG) estimates for all other members get probabilistic clipping, not DP noise

#### Sources

- arXiv 2409.04652
- Link: <https://arxiv.org/abs/2409.04652>

---

## D61

### U.S. Census Bureau: OnTheMap

**My tier rating:** Tier 3

#### Basic information (Tier 1)

- **Name:** OnTheMap
- **Data curator:** U.S. Census Bureau
- **Type of data curator:** Government
- **Publication year:** 2008
- **Still to be filled:** intended use; data product type; region; sector

#### DP variant and privacy loss (Tier 2)

- **DP variant:** Approximate (ε, δ)
- **Privacy unit:** One worker (one row of the commuting table)
- **Privacy parameters:** ε = 8.6, δ = 1 × 10^-5
- **Deployment model:** Central

#### Tier 3 details

Public totals and domain coarsening and restriction (domain). One commuter record (unit). (epsilon, delta) probabilistic DP with pruning (accounting). Multinomial-Dirichlet synthesis (mechanism). Reasons why other definitions were unsuitable. Workplace data protected by separate noise infusion (unprotected). Source: Machanavajjhala et al., ICDE 2008.

- **Still to be filled:** data domain; unprotected quantities; trust assumptions; release type and its details; data source (static or dynamic); access type; post-processing

#### Evidence from the organization's own documents

ICDE 2008 paper (with Census staff), exact words: 'The overall ε for the procedure was 8.6 and disclosure probability δ was = 0.00001', under (ε, δ)-probabilistic differential privacy, where datasets differ in one row (one worker). These values come from the paper's experiments on public OnTheMap data for Minnesota. A Census LEHD presentation (Nov 2008) gives nominal ε* = 4.6, δ = 0.000001 and 'ε < 9 in all cases with 99.99999% confidence'. Other sources: Desfontaines says John Abowd confirmed the paper's parameters were used in the deployment. Status (Census Director's blog, Aug 17, 2026): under Commerce Department Administrative Order 216-26 (June 2026), 'noise infusion is no longer allowed' for new Census-disseminated products, which will use coarsening and suppression instead; LEHD products 'produced with noise infusion required by states in our data-sharing agreements will continue until these agreements are updated'

#### Gaps

Uses probabilistic DP, a weaker variant. The paper's numbers come from experiments; the production values appear only in a 2008 presentation (different values) and in personal correspondence reported by Desfontaines. No current production settings published

#### Sources

- Machanavajjhala, Kifer, Abowd, Gehrke and Vilhuber, ICDE 2008; Census LEHD presentation (IAB workshop, Nov 2008)
- Link: <https://ptolemy.berkeley.edu/projects/truststc/pubs/463/icde2008-privacy.pdf>

---

## D69

### Wikimedia Foundation: Wikipedia editor statistics (monthly)

**My tier rating:** Tier 3

#### Basic information (Tier 1)

- **Name:** Wikipedia editor statistics (monthly)
- **Data curator:** Wikimedia Foundation
- **Type of data curator:** Non-profit
- **Publication year:** 2023
- **Still to be filled:** intended use; data product type; region; sector

#### DP variant and privacy loss (Tier 2)

- **DP variant:** Pure
- **Privacy unit:** One editor's contribution (per country, project and month)
- **Privacy parameters:** ε = 2
- **Deployment model:** Central

#### Tier 3 details

Unit options compared; chosen unit is editor-project-country-month. Laplace histogram (mechanism). Public country and project lists (domain). One unit of loss per (country, project, month) per editor (accounting). Reasons in the feasibility and release-prioritization pages. Sources: Wikimedia Meta-wiki feasibility report; README.

- **Still to be filled:** data domain; unprotected quantities; trust assumptions; release type and its details; data source (static or dynamic); access type; post-processing

#### Evidence from the organization's own documents

Wikimedia README, exact words: 'Privacy budget: epsilon = 2. Epsilon is 1.1 for count and 0.9 for sum for lower risk countries, 0.2 for medium risk countries and 0.1 for higher risk countries', using 'Laplace pure DP'; 'the privacy loss of an individual editor's contribution to the dataset will be limited to a worst-case of epsilon = 2'. Rows below 8/45/95 editors are dropped. Other sources: Desfontaines agrees on ε = 2

#### Gaps

Wikimedia says privacy loss grows if a person uses several accounts, projects or countries. The weekly dataset adds loss for each overlapping week; the weekly README puts the combined loss at 4 or 6, but the monthly README gives no combined total. ε = 2 applies only to lower-risk countries; no total across months

#### Sources

- Wikimedia Geoeditors Differential Privacy — Monthly README
- Link: <https://analytics.wikimedia.org/published/datasets/geoeditors_monthly/00_README.html>

---

## D70

### Wikimedia Foundation: Wikipedia editor statistics (weekly)

**My tier rating:** Tier 3

#### Basic information (Tier 1)

- **Name:** Wikipedia editor statistics (weekly)
- **Data curator:** Wikimedia Foundation
- **Type of data curator:** Non-profit
- **Publication year:** 2023
- **Still to be filled:** intended use; data product type; region; sector

#### DP variant and privacy loss (Tier 2)

- **DP variant:** Pure
- **Privacy unit:** One editor's contribution (per country, project and week)
- **Privacy parameters:** ε = 2
- **Deployment model:** Central

#### Tier 3 details

Same documentation family as the monthly release (Meta-wiki Geoeditors project pages and the weekly README).

- **Still to be filled:** data domain; unprotected quantities; trust assumptions; release type and its details; data source (static or dynamic); access type; post-processing

#### Evidence from the organization's own documents

Wikimedia weekly README, exact words: 'Privacy budget: epsilon = 2', with Laplace pure DP (ε = 1.1 for editor counts and 0.9 for edit sums); 'the privacy loss of an individual editor's contribution to the dataset will be limited to a worst-case of epsilon = 2'. Combined with the monthly release: 'In most cases, months will entirely contain a week (meaning a cumulative privacy loss of 4), but sometimes, 2 months will overlap with a given week (yielding a cumulative privacy loss of 6).' First release July 2023; rows below 8 editors dropped. Other sources: Desfontaines agrees on ε = 2

#### Gaps

Privacy loss grows if a person uses several accounts, projects or countries (Wikimedia says so). The combined loss with the monthly data is 4 or 6 per week, but there is no total across weeks or months. The caveat names 'geoeditors_weekly' where it means the monthly dataset, a small error in the document. Unlike the monthly README, this one does not mention different ε for medium- or higher-risk countries

#### Sources

- Wikimedia Geoeditors Differential Privacy — Weekly README (screenshot provided Nov 2026)
- Link: <https://analytics.wikimedia.org/published/datasets/geoeditors_weekly/00_README.html>

---

## D65

### Microsoft with IOM: Global Victim-Perpetrator Synthetic Dataset

**My tier rating:** Tier 2

#### Basic information (Tier 1)

- **Name:** Global Victim-Perpetrator Synthetic Dataset
- **Data curator:** Microsoft with IOM
- **Type of data curator:** Non-profit
- **Publication year:** 2022
- **Still to be filled:** intended use; data product type; region; sector

#### DP variant and privacy loss (Tier 2)

- **DP variant:** Approximate (ε, δ)
- **Privacy unit:** One victim in the original data
- **Privacy parameters:** ε = 12, δ = 5.8 × 10^-6
- **Deployment model:** Central

#### Tier 3 details

Not all Tier 3 details are disclosed in the organization's own sources, so this entry is rated Tier 2.

#### Evidence from the organization's own documents

IOM dashboard for this dataset, exact words in its 'About synthetic data' pop-up: protects trafficked persons 'via differential privacy (ε=12, δ=5.8 x 10-6)'. The dashboard header says it protects '~18k actual trafficked persons assisted by IOM from 2005 to 2022'. IOM codebook (v1, Dec 2022): built with Microsoft's Synthetic Data Showcase from DP counts of short attribute combinations; 'the unit of observation is at the individual (trafficking victim) level'. The codebook, dataset page and Microsoft's blog give no ε. Other sources: Desfontaines and later papers cite the same ε = 12, δ = 5.8 × 10⁻⁶. IOM's newer Global Synthetic Dataset (2024, a different dataset) states ε=12, δ=3.57 x 10^-7

#### Gaps

The ε appears only in a dashboard pop-up whose text names 'The Global Synthetic Data' and '~206K' persons, not this dataset of about 18,000 victims, so it seems copied from another dataset. The codebook, dataset page and Microsoft's blog give no ε. IOM says total privacy loss across releases is the sum of each budget, but gives no running total. Protection is per victim; IOM notes it cannot tell whether the same perpetrator appears in several victims' accounts. The pop-up itself lists 'no accuracy guarantee' and 'possibility of spurious combination release' as disadvantages

#### Sources

- IOM CTDC Global Victim-Perpetrator Synthetic Data dashboard ('About synthetic data' pop-up, screenshot Nov 2026); IOM codebook v1 (Dec 2022)
- Link: <https://www.ctdatacollaborative.org/global-victim-perpetrator-synthetic-dataset>

---

## D68

### Wikimedia Foundation: Russian editor information (one-off release)

**My tier rating:** Tier 2

#### Basic information (Tier 1)

- **Name:** Russian editor information (one-off release)
- **Data curator:** Wikimedia Foundation
- **Type of data curator:** Non-profit
- **Publication year:** 2023
- **Still to be filled:** intended use; data product type; region; sector

#### DP variant and privacy loss (Tier 2)

- **DP variant:** Pure
- **Privacy unit:** One editor account, per month
- **Privacy parameters:** ε = 0.1
- **Deployment model:** Central

#### Tier 3 details

Not all Tier 3 details are disclosed in the organization's own sources, so this entry is rated Tier 2.

#### Evidence from the organization's own documents

Wikimedia (Wikitech page), exact words: data for Russia was taken from geoeditors_monthly with 'Laplace noise (epsilon = 0.1, sensitivity = 1, noise scale = 10)', and 'for each account that someone uses, and for each month they use it, their worst-case privacy loss will increase by 0.1.' Other sources: Desfontaines agrees on ε = 0.1

#### Gaps

A person with several accounts loses more privacy (Wikimedia gives this example). One-off release; Tier 3 detail not confirmed

#### Sources

- Wikitech page on the release
- Link: <https://wikitech.wikimedia.org/wiki/Russian_editor_information_(2022-23)>

---

## D76

### UK Office for National Statistics: Differentially private synthetic linked 2011 Census and mortality data (Integrated Data Service)

**My tier rating:** Tier 2

#### Basic information (Tier 1)

- **Name:** Differentially private synthetic linked 2011 Census and mortality data (Integrated Data Service)
- **Data curator:** UK Office for National Statistics
- **Type of data curator:** Government
- **Publication year:** 2023
- **Still to be filled:** intended use; data product type; region; sector

#### DP variant and privacy loss (Tier 2)

- **DP variant:** Approximate (ε, δ)
- **Privacy unit:** One individual (one row)
- **Privacy parameters:** ε = 1, δ = 1 × 10^-8
- **Deployment model:** Central

#### Tier 3 details

Not all Tier 3 details are disclosed in the organization's own sources, so this entry is rated Tier 2.

#### Evidence from the organization's own documents

ONS Data Science Campus report (Nov 2023), exact words: MST adheres to Rényi DP with 'the upper bound ε and a cryptographically small failure probability δ'; δ set to 10^−ceil(log10 N), giving 'our δ = 10⁻⁸', and 'Ultimately, we chose to use ε = 1', with σ ≈ 56 noise per marginal cell. Integrated Data Service catalogue: 'The privacy budget, epsilon = 1.0', available only to provider approved projects. Other sources: none found that disagree. The registry's 'Synthetic Data for Public Use' entry describes a 2020 GAN recommendation, not this dataset

#### Gaps

Privacy unit not defined explicitly; the report speaks of an individual's privacy and the data has one row per person. ε was chosen after testing utility on the confidential data. Access limited to accredited researchers, so not a public release

#### Sources

- ONS Data Science Campus report (Nov 2023); Integrated Data Service catalogue
- Link: <https://datasciencecampus.ons.gov.uk/synthesising-the-linked-2011-census-and-deaths-dataset-while-preserving-its-confidentiality/>

---

## D78

### Meta: Movement Distribution Maps

**My tier rating:** Tier 2

#### Basic information (Tier 1)

- **Name:** Movement Distribution Maps
- **Data curator:** Meta
- **Type of data curator:** Tech company
- **Publication year:** 2022
- **Still to be filled:** intended use; data product type; region; sector

#### DP variant and privacy loss (Tier 2)

- **DP variant:** Pure
- **Privacy unit:** One person, one day (one ping sampled per person)
- **Privacy parameters:** ε = 1
- **Deployment model:** Central

#### Tier 3 details

Not all Tier 3 details are disclosed in the organization's own sources, so this entry is rated Tier 2.

#### Evidence from the organization's own documents

Meta Data for Good readme (Dec 2022), exact words: 'Since we sample a single ping per person, the sensitivity of each count ... is 1. This means that we can implement differential privacy with epsilon = 1 by adding Laplace noise with strength 1 to these counts'; polygons are released only if the noisy person count exceeds 10. Successor to Movement Range Maps. Other sources: none found that disagree

#### Gaps

Meta says DP 'is not incorporated into the estimation of people's homes', so home assignment is outside the guarantee. Daily releases with no total budget across days. Tier 3 detail borderline

#### Sources

- Data for Good at Meta, dataset readme (HDX)
- Link: <https://data.humdata.org/dataset/32167ba5-ef67-4254-8eaf-04cdb8b90c1d/resource/767a05fe-0bf6-4a0b-96dc-8525baefa327/download/movement-distribution-readme-data-for-good-at-meta.pdf>
