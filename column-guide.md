# Column guide

What each column in `deployments.csv` and the main sheet of `dp-deployments-dataset.xlsx` means.

| Column | What it means |
|---|---|
| ID | Row number for the deployment (D01, D02, ...) |
| Organization | Who runs the deployment |
| Type of organization | Tech company, Government, or Non-profit (including international groups) |
| System or dataset | The name of the DP system or data release |
| Year | Year the deployment or release started, as stated in the sources. Blank means no source gives a year |
| ε, δ, ρ | Tier 2 detail 1, the privacy parameters, exactly as the organization's own source states them. Blank means the organization does not publish it. Other sources' values are in the Notes |
| Privacy unit (what is protected) | Tier 2 detail 2. For example one person, or one user's data for one day |
| Type of DP | Tier 2 detail 3. Pure (ε only), Approximate (ε and δ), zCDP (ρ), Set by customer, No formal DP guarantee, or Not stated |
| Deployment model (where the noise is added) | Tier 2 detail 4. Local (on the device), Central (by the organization), Distributed, or Federated |
| Tier (registry's three tiers) | Uses the registry's three tiers (registry.opendp.org/transparency-tiers). Tier 1: basic facts only. Tier 2: all four key details are public. Tier 3: Tier 2 plus more detail on the privacy unit, accounting, implementation and the reasons for choices. Worked out by formula from the columns above and the Tier 3 evidence column |
| Missing details | Which of the four key details are not public. None means the deployment reaches Tier 2 |
| Gaps (what the organization's sources do not say) | Everything the organization's own sources leave out for this deployment, across all columns, including Tier 3 items. Other sources that fill a gap are named in the Notes |
| Tier 3 evidence | Where the Tier 3 detail was found: in the registry, or in the deployment's own sources. No means not found in what I read, not that it does not exist. Not confirmed or Borderline means I could not settle it. Not applicable means the deployment is below Tier 2, so it cannot be Tier 3 |
| What the sources show (Tier 3 items) | The evidence behind the Tier 3 check, with the sources. Blank when the registry already shows it or the deployment is below Tier 2 |
| In the registry? | Yes if the deployment is in the official DP Deployments Registry (data downloaded November 2026) or its earlier prototype, with the prototype tier where known. No if it is in neither |
| In Desfontaines's list? | Whether it appears in Damien Desfontaines's public list (August 2025 version, re-checked November 2026) |
| Checked against original source? | Yes if the original paper, blog post or document was read and matches. Partly if only some values could be confirmed |
| Notes | Disagreements between sources and how each value was chosen. A Tier note explains where my tier differs from the registry's own rating |
| Source, Link | Where the values came from |
