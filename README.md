## PFOCR Pipeline Post-processing and Publishing

This README describes how to process new batches of results from the PFOCR pipeline and release them in useful formats.

1. Process figures 
  - Starts with latest rds, e.g., "pfocr_figures_20210515.rds"
  - Unifies the column names. It also formats the PMC filename and image link to work with NDEx.
  - Removes some unnecessary columns
  - Removes preambles from fig titles
  - Determins unique figure "number" and figtype for all figures
  - Adds figid_alias for GMTs and other human-readable use cases
  - Replaces empty/NA , <25, >200 fig titles
  - Applies ungreek function
  - reconciles organism/species names
  - Checks for missing titles
  - Checks for titles that are too short / too long
  - Checks for special cases, like (A) at the beginning of captions, artifacts
  - Final RDS of new and old content merged: pfocr_figures_draft.rds
  
2. Process genes
  - Starts with latest rds, e.g., "pfocr_genes_20210515.rds"
  - Double check values of pmc_id, hgnc_symbol and lex_source for new entries!
  - Double check proper expansion of bioentities!
  - Unifies the column names
  
3. Check checmicals and disease (from PubTator)
  - TODO

4. Generate GMTs
  - Run pfocr_gmt.R
  - Produce "filtered" gmt with hgnc3 subset for human and mouse.

5. Generate annots from Jensen enrichment
  - Run pforc_enrich.R
  - Uses gmt from prior step
  - check printed stats along the way. Certainly room for improvement here.
  - Produce pfocr_annots_draft.rds
  
6. Update ShinyApps.io
  - Run pfocr_shiny.R
  - Uses genes, figures, and annots from prior steps
  - Copy draft rds over to shiny app dir and rename (remove _draft)
  - Test app and publish to shinyapps.io

7. Push to NDEx
  - TODO

8. Publish on Figshare?
  - TODO
