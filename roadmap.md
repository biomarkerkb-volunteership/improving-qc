**Week 1 (complete)** - Kick-off and onboarding

---

**Week 2 - Environment and tooling setup**
- Register on GitHub (if not already) and share your username
- Get access to the biomarker-qc repository; clone it and confirm `biomarker-qc.py` runs on your machine
- Read through the README so you understand what checks the script currently runs
- Familiarize yourself with both TSV files (`oncomx.tsv` and `sennet.tsv`) - just browse them, no changes yet
- Define the contribution workflow: you'll document issues and proposed corrections in a corrections file (CSV with columns for row number, field, current value, proposed value, and reasoning); direct TSV edits are handled by the mentor

---

**Week 3 - Understand the existing QC and fork data-qc**
- Fork the [data-qc](https://github.com/clinical-biomarkers/data-qc) repository on GitHub
- Read through `main.py` and `qc_checks.py` carefully - understand exactly what each check does and does not cover
- Run data-qc and `biomarker-qc.py` on `oncomx.tsv` - observe what each flags
- **Crucially:** the data has known issues that the existing QC does not catch. Cross-reference the QC output against the actual data and start identifying gaps - what kinds of errors slip through?
- Begin a running notes document listing: (a) issues you found in the data, and (b) what new or improved QC check could have caught them

---

**Week 4 - `oncomx.tsv` deep review and new QC proposals**
- Continue the row-by-row review of `oncomx.tsv`, focusing on issues the existing scripts miss. Known gaps to investigate:
  - LYMP/LMYPH inconsistency (a string normalization issue the current script doesn't catch)
  - Biomarker IDs shared across records that should be distinct, incorrectly forming panel biomarkers
  - Lymphocyte records with different conditions collapsed under the same ID
  - Disease names mismatched to their DOID (e.g. DOID:1612 is breast cancer, not advanced cancer)
  - Conflicting accessions or entity types under the same ID
  - assessed_biomarker_entity not matching the biomarker string (e.g. HGF record with IL6 in the entity field)
  - Wrong entity types
  - Examples of issues can be viewed here: https://github.com/clinical-biomarkers/biomarker-issue-repo/issues/29
- For each issue found: document the correction in the corrections file, and add a proposed new QC check to your notes document
- Submit the oncomx corrections file; mentor applies changes and provides feedback

---

**Week 5 - `sennet.tsv` QC and evidence sentence extraction**
- Apply the same approach to `sennet.tsv`: run both QC scripts, note what they catch vs. what they miss
- The main known gaps in sennet: missing biomarker directionality (entries say "CDKN1A" rather than "increased CDKN1A expression"), and missing evidence sentences
- Coordinate with co-mentor to run the LLM-based sentence extraction tool on flagged rows
- Continue adding to the running notes document: what new checks would catch directionality issues or missing evidence?

---

**Week 6 - `sennet.tsv` curation and QC proposal write-up**
- Add directionality to the biomarker field for each sennet entry using the extracted evidence sentences
- Resolve any other issues surfaced during the sennet review
- Submit the sennet corrections file
- Begin consolidating the running notes into a structured QC proposal: for each proposed new check, describe what it catches, why the current scripts miss it, and a sketch of how it could be implemented

---

**Week 7 - Final review and symposium handoff**
- Cross-dataset consistency check: IDs, controlled vocabulary, and format alignment across both TSVs
- Buffer time for any late-surfacing issues
- Finalize the QC proposal document and combined issue log - this becomes the core material for the week 8 symposium presentation

---

**Week 8 (dedicated)** - Symposium presentation preparation

---
