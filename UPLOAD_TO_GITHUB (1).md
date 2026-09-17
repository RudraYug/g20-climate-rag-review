# Uploading this anonymised package to GitHub

1. Create a new private or anonymised review repository from an account that does not reveal author identity.
2. Upload the contents of this directory, not the parent folder and not any previous `.git` history.
3. Keep the repository private unless the journal permits an anonymous public link.
4. Select a data/code licence only after confirming the journal and source-document requirements.
5. Run:

```bash
python scripts/validate_repository.py .
```

6. Confirm that `passes_review_package_structure` is `true`.
7. Do not claim full reproducibility until `passes_full_reproduction_package` is `true`.
8. Freeze the release and retain `MANIFEST.sha256`.
9. Insert the view-only anonymous URL in the manuscript.

The raw UNFCCC and IPCC PDFs are not redistributed. Use a completed corpus manifest with official links.
