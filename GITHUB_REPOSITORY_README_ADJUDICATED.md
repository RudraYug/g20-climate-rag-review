# G20 Climate-Policy Evidence RAG - Review Repository

## Purpose

This repository accompanies the paper **Evidence-Grounded RAG for G20 Climate-Policy Retrieval, Cited Synthesis and Human-Supervised Gap Screening**. The heatmap is a first-pass screening aid, not a validated autonomous policy classifier.

## Start here

1. `manuscript/submission_manuscript_cambridge_a_adjudicated_v1.0.pdf`
2. `manuscript/supplementary_material_adjudicated_v1.0.pdf`
3. `data/questions/final_adjudicated/README` (this directory is documented by `data/questions/README.md`)
4. `audit/REFERENCE_SET_ADJUDICATION_REPORT.md`
5. `audit/RAW_ARTIFACT_RECOVERY_REPORT.md`
6. `audit/NUMERICAL_CROSSCHECK.md`
7. `REPOSITORY_STATUS.csv` and `VALIDATION_REPORT.json`

## Frozen 80-question reference set v1.0

The original review produced 21 Full, 50 Partial and 9 None outcomes. All 59 Partial/None cases were checked against the cited frozen-corpus evidence and resolved into 17 Clarify, 30 Revise and 12 Reconstruct dispositions. The final 80-item set is stored under `data/questions/final_adjudicated/`. Four flawed question premises were corrected for future use.

The resource is a **source-adjudicated within-study reference set**, not a multi-expert consensus gold standard. The revised answers were not independently reconfirmed by the reviewer. Pre-adjudication files remain under `data/questions/history_pre_adjudication/`.

## Reference-dependent metric update

ROUGE metrics were recomputed against v1.0 and are under `data/evaluation/reference_metrics_v1.0/`. The previous broad lexical-overlap advantage for no-RAG largely disappeared: ROUGE-1 and ROUGE-2 show no statistically detectable paired difference; no-RAG remains modestly higher on ROUGE-L. BERTScore and RAGAS Context Precision/Recall were not rerun and are excluded from final reporting. The automated claim-label rates did not change.

## Raw records recovered

- 80 GPT-4o no-RAG outputs.
- 80 GPT-4o+RAG outputs.
- 80 Mistral+RAG and 80 LLaMA+RAG outputs.
- Per-question claim-category counts for all four conditions.
- 579 atomic no-RAG claim records with text, GPT-4o-mini label and reason.

The original RAG evaluation stored category counts but did not preserve the individual extracted RAG claim strings or judge reasons. Those missing records were not reconstructed.

## Key directories

- `data/questions/final_adjudicated/`: frozen 80-item reference set v1.0 and 59-item adjudication log.
- `data/questions/history_pre_adjudication/`: original author-prepared answers and independent-review outcomes.
- `data/evaluation/reference_metrics_v1.0/`: recomputed per-query ROUGE values and paired bootstrap results.
- `data/evaluation/failure_taxonomy_v1.0/`: updated question-level primary outcomes.
- `data/outputs/`: recovered canonical model outputs.
- `data/claims/`: atomic no-RAG claims and per-question category-count tables.
- `data/heatmap/`: original and D6-audited matrices, evidence and pilot-review files.
- `data/d6_transport/`: original D6 labels and 17-cell source audit.
- `src/`: recovered implementation source.
- `prompts/`: recovered prompts; the exact no-RAG prompt text was not found and is not reconstructed.
- `scripts/`: metric reproduction, adjudication and repository validation.
- `audit/`: adjudication, recovery, numerical and source-archive audit records.

## Reproduce

```bash
python scripts/recompute_claim_metrics.py --repo-root .
python scripts/adjudication/recompute_reference_metrics.py
python scripts/adjudication/recompute_failure_taxonomy.py
python scripts/validate_repository.py
```

## Interpretation boundaries

- Formal heatmap agreement metrics cover 8 of 119 cells.
- Claim labels are GPT-4o-mini estimates against author-prepared evidence packages.
- The no-RAG archive identifies `gpt-4o-2024-08-06`; the RAG archive records only `gpt-4o`.
- Raw NDC/IPCC PDFs are not redistributed.
- The populated Chroma SQLite file is over 100 MB and is not included in the ordinary GitHub repository; see `data/indexing/VECTORSTORE_STATUS.md`.
