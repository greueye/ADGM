This project is a Jupyter-friendly document review tool for ADGM corporate agents.
It scans uploaded .docx documents for:

Jurisdiction mismatches (non-ADGM courts)
Ambiguous terms (e.g., may, should, endeavour)
Missing signature blocks
Required incorporation documents checklist

The tool uses python-docx for Word document parsing and Gradio for an inline web UI directly inside Jupyter Notebook.

# Features

Upload multiple .docx files at once
Detect document type using keyword matching
Identify “red flag” compliance issues:
References to non-ADGM jurisdictions
Ambiguous legal terms
Missing signature blocks
Auto-generate reviewed Word files with comments inserted
Show JSON structured report of issues
Identify missing required incorporation documents
Inline operation inside Jupyter Notebook (no external browser required)

# Setup Instructions

Prerequisites
Python 3.9+
Jupyter Notebook / JupyterLab
Microsoft Word (optional, to open .docx results)

 # Running the App in Jupyter

Copy the final Python script into a Jupyter Notebook cell.
Run the cell — Gradio will launch inline (inline=True).
Upload one or more .docx files via the UI.
Click Run Review.
Download:
Reviewed .docx / .zip — contains inserted comment paragraphs for flagged issues.
JSON report — structured list of all issues + checklist status.

# Example Test Documents

Articles_of_Association.docx → mostly clean, valid signature.
Board_Resolution.docx → contains non-ADGM jurisdiction.
Shareholder_Resolution.docx → ambiguous term “may” + missing signature.

# Code Flow
Step 1 — Initial Prototype
Started with a Python prototype that processed .docx files using python-docx.
Detected document type based on keywords.
Checked for patterns (jurisdiction, ambiguous words, missing signature).
Returned issues in console output.

Step 2 — Adding Review Comments
Modified code to insert inline comment paragraphs in the reviewed .docx output.
Added document-level issues at the end of the file.
Stored reviewed output in memory for download.

Step 3 — Multi-File Processing
Added ability to handle multiple .docx uploads.
Zipped reviewed files when multiple documents are uploaded.
Introduced required documents checklist for incorporation.

Step 4 — Gradio Web UI
Converted the script into a Gradio app with:
File uploader
JSON report display
Reviewed file download
Configured demo.launch(share=False, inline=True) for Jupyter inline display.

Step 5 — Bug Fixes & Compatibility
Fixed syntax errors ("Unknown Document Type" string bug).
Fixed Gradio gr.File return type issue (only return file path, not tuple).
Ensured Gradio 4.x compatibility.
Tested with generated sample .docx files.
