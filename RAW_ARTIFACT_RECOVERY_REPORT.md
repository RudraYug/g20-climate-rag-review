# Raw generation and claim-record recovery audit

## Scope

The supplied `data.zip`, `chroma_db.zip`, seven code archives, `table8_recomputed.csv` and `table9_gpt4o_vs_llama.csv` were searched structurally and by content.

## Recovered artefacts

1. **Canonical model outputs**
   - 80 GPT-4o no-RAG outputs in `ragas_results_no_rag.json`.
   - 80 GPT-4o+RAG, 80 Mistral+RAG and 80 LLaMA+RAG outputs in `rq3_results.json`.
   - 412 additional historical GPT-4o response traces were found. Only 38 exactly match a canonical final GPT-4o answer, so they are preserved separately and are not substituted for the final 80-row set.

2. **Claim-level records**
   - 579 no-RAG claims were recovered with claim text, GPT-4o-mini label and judge reason.
   - For all four model conditions, per-question counts of Supported, Partial, Unsupported and Fabricated claims were recovered.
   - Individual RAG claim strings and judge reasons were not stored. `rq3_comparison.py` serialised category counts only; those missing records were not reconstructed.

3. **Reproduced pooled estimates**
   - GPT-4o no-RAG: 243 Unsupported/Fabricated claims out of 579 = **0.4196891192**.
   - GPT-4o+RAG: 71/463 = **0.1533477322**.
   - Mistral+RAG: 70/433 = **0.1616628176**.
   - LLaMA+RAG: 99/448 = **0.2209821429**.
   - These counts reproduce the final no-RAG/RAG and GPT-4o/LLaMA point estimates. They additionally support a pooled Mistral estimate that was previously omitted.

4. **ROUGE denominator resolution**
   - GPT-4o ROUGE-1 F1 across all 80 rows: **0.2821**.
   - Mistral across all 80 rows: **0.2398**; the earlier 0.2428 summary excludes one 503 response.
   - LLaMA across all 80 rows: **0.2377**; the earlier 0.2663 summary averages the 71 non-insufficient responses rather than all 80.
   - The updated manuscript uses all-80 ROUGE values and reports latency over successful API calls.

5. **Model metadata**
   - The no-RAG archive records `gpt-4o-2024-08-06`.
   - The RAG archive records only the `gpt-4o` alias. Exact snapshot equality cannot be verified.

6. **Bootstrap code**
   - `src/evaluation/bootstrap_ci.py` is a legacy Bernoulli simulation from old aggregate rates.
   - `scripts/recompute_claim_metrics.py` uses the recovered paired question-level counts and reproduces the manuscript's rounded confidence intervals and p-values.

7. **Vector stores**
   - The separate `chroma_db.zip` is empty.
   - The populated vector store is inside `data.zip` and contains 4,705 embeddings. Its SQLite file exceeds GitHub's normal per-file size limit and is documented rather than included.

## Publication boundary

The repository can state that raw canonical outputs and per-question claim counts are available and that pooled point estimates and question-cluster bootstrap statistics can be recomputed. It must still disclose that atomic RAG claim text/reasons and an exact dated RAG GPT-4o model identifier are unavailable.
