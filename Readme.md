# Internship Project

This repository contains my internship google colab notebooks and code.

# English–Punjabi Agromet Advisory Bulletin Pipeline

OCR, alignment, and quality validation pipeline for English–Punjabi Agromet Advisory Bulletins (IMD/PAU) across 20 Punjab districts. Built during internship at CSIR-CSIO Chandigarh.

## Pipeline

**1. OCR** — Punjabi PDFs and English pdfs. Fixed by forcing image-based OCR (Tesseract) instead of trusting the embedded text layer.

**2. Alignment** — Matched 618 English–Punjabi bulletin pairs by district + date. Used a language-agnostic heading classifier (90+ heading variants, 15 categories) + LaBSE embeddings to align sections by meaning, fixing silent misalignment from page-break fragmentation and section renumbering. Output: per-pair Excel with Section ID, English/Punjabi heading & content.

**3. Validation** — Back-translated Punjabi → English, compared against original English using 8 metrics:
- **Semantic**: BERTScore, Cosine Similarity
- **Lexical**: BLEU, chrF++, ROUGE-L, METEOR
- **Domain**: Entity Preservation, Numeric Consistency

Classified as Pass (Excellent/Good) or flagged for manual review based on BERTScore/Cosine thresholds.

## Tech Stack
Python, Tesseract, Docling, LaBSE, sentence-transformers, Google Cloud Translation API / IndicTrans2

## Output
Aligned bilingual Excel files, missing-pair report, scored validation results + summary report (JSON/Markdown)
