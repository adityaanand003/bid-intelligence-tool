# Procurement Data Extraction Tool

Automates extraction of structured data from procurement documents (RFPs, amendments, Q&As, specs) using Google Gemini AI.

## Requirements

- pdfplumber
- beautifulsoup4
- lxml
- google-generativeai
- Google Gemini API key

## Installation

```bash
pip install pdfplumber beautifulsoup4 lxml google-generativeai
```

## Extracted Fields

 - Bid Number
 - Title
 - Due Date
 - Bid Submission Type
 - Term of Bid, Pre Bid Meeting
 - Installation, Bid Bond Requirement
 - Delivery Date, Payment Terms
 - Any Additional Documentation Required
 - MFG for Registration
 - Contract or Cooperative to use
 - Model_no
 - Part_no
 - Product
 - contact_info
 - company_name
 - Bid Summary
 - Product Specification

## Usage

1. Place procurement documents (PDF/HTML) in a folder
2. Update API key in notebook
3. Set folder path and output filename
4. Run cells to generate JSON output

```python
folder_to_process = './data/Bid1'
output_filename = 'Bid1_output.json'

all_text = get_all_text_from_folder(folder_to_process)
extracted_json_string = get_json_from_llm(all_text, field_list_str)

json_data = json.loads(extracted_json_string)
with open(output_filename, 'w', encoding='utf-8') as f:
    json.dump(json_data, f, indent=2, ensure_ascii=False)
```

## Features

- Processes multiple PDF and HTML files
- Prioritizes latest information from amendments
- Synthesizes data from multiple documents
- Returns null for missing data (no guessing)
- Outputs clean JSON format

## Folder Structure

```
project/
├── try stuff out.ipynb
├── data/
│   ├── Bid1/
│   └── Bid2/
├── Bid1_output.json
└── Bid2_output.json
```
