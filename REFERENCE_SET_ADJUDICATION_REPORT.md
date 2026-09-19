# Reference-set adjudication report

## Scope

The original 80-question review produced 21 Full, 50 Partial and 9 None outcomes. The 59 flagged cases were source-adjudicated against the frozen NDC/IPCC corpus.

## Final dispositions

- Retain (original Full agreement): 21
- Clarify: 17
- Revise: 30
- Reconstruct: 12
- Total final frozen set: 80
- Question premises corrected for future use: 4

## Status

The output is frozen as **source-adjudicated within-study reference set v1.0**. It is not described as a multi-expert gold standard because the revised answers were not returned to the reviewer for independent confirmation.

## Metric impact

Reference-dependent ROUGE metrics were recomputed against v1.0. The earlier broad ROUGE advantage for no-RAG largely disappeared: ROUGE-1 and ROUGE-2 differences are not statistically detectable, while no-RAG remains modestly higher on ROUGE-L. BERTScore and RAGAS Context Precision/Recall were not rerun and are excluded from final reporting. Automated claim-label rates are unchanged because they depend on the common evidence packages and judge labels rather than reference-answer wording.

## Reproducibility

The final 80-item CSV, 59-item log, compatible JSON, workbook, scripts and version manifest are included in the repository.
