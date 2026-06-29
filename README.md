# 📊 Company Insight Processor

**A Python tool for analysing company outsourcing needs – with an interactive menu, smart filtering, and beautiful PDF reports.**

[![Python 3.6+](https://img.shields.io/badge/python-3.6+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![GitHub repo](https://img.shields.io/badge/GitHub-akashkarn9486/company--analysis--brightgreen)](https://github.com/akashkarn9486/company-analysis-)

**Visit the repository:** [akashkarn9486/company-analysis-](https://github.com/akashkarn9486/company-analysis-)

---

## 📖 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Requirements](#requirements)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [Input CSV Format](#input-csv-format)
- [Output Reports](#output-reports)
  - [PDF Report](#pdf-report)
  - [CSV / Excel](#csv--excel)
- [AI‑Driven Analysis](#aianalysis)
- [Interactive Walkthrough](#interactive-walkthrough)
- [Customisation](#customisation)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)

---

## 🔍 Overview

The **Company Insight Processor** loads a CSV dataset of companies and lets you interactively filter, sort, and analyse their outsourcing needs. It generates a professional **PDF report** (or CSV/Excel) that includes:

- A **summary** with industry and company size distributions.
- **Top 10 outsourcing needs** across all companies.
- **Industry‑specific insights** – the most common outsourcing requirements for each major sector.
- A **full data table** with **wrapped LinkedIn URLs** (no text overflow).
- A **visitor counter** that persists across sessions (increments every time a PDF is generated).
- A **styled header** with your name and a coloured banner.

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| **Interactive menu** | No command‑line hassle – just answer a few questions. |
| **Filtering** | By company name (substring), industry, or company size. |
| **Sorting** | Sort by any column (e.g., Company Name, Industry, Company Size). |
| **Multiple export formats** | PDF, CSV, or Excel. |
| **PDF with visual elements** | Coloured header, decorative line, visit counter, date footer. |
| **Persistent visitor counter** | Stored in `visitor_count.txt` – increases with each PDF generation. |
| **Wrapped URLs** | LinkedIn links are automatically wrapped inside table cells. |
| **AI‑driven insights** | Frequency analysis of outsourcing needs per industry. |
| **Preview before saving** | See the first 5 rows and summary before generating the report. |

---

## 📦 Requirements

- **Python 3.6+**
- **pip** (Python package manager)

Install the required libraries:

```bash
pip install pandas openpyxl reportlab
```

| Library    | Purpose                     |
|------------|-----------------------------|
| `pandas`   | Reading and processing CSV data |
| `openpyxl` | Exporting to Excel (`.xlsx`) |
| `reportlab`| Generating PDF reports       |

---

## 🚀 Installation

1. **Clone this repository** (or download the script directly):
   ```bash
   git clone https://github.com/akashkarn9486/company-analysis-
   cd company-analysis-
   ```

2. **Place your CSV file** in the same folder as the script.  
   The default filename is `company_dataset_10000.csv` – you can use a different name and specify it when prompted.

3. **Install dependencies** (if not already done):
   ```bash
   pip install pandas openpyxl reportlab
   ```

---

## 🏃 Quick Start

Run the script **without any arguments**:

```bash
python company_insight_processor.py
```

Then follow the interactive prompts:

1. **Enter your name** – appears in the PDF header.
2. **Input CSV path** – press Enter to accept the default (`company_dataset_10000.csv`) or type a full/relative path.
3. **Output file** – defaults to `report.pdf`.
4. **Filter options** – choose by name substring, industry, or none.
5. **Optional size filter** – e.g., `Large`, `Enterprise`.
6. **Sort column** – defaults to `Company Name`.
7. **Report format** – `pdf`, `csv`, or `excel` (default: `pdf`).
8. The script shows a summary and a preview; confirm to generate the report.

---

## 📁 Input CSV Format

The CSV **must** contain these exact column headers:

| Column Name        | Description                                                      |
|--------------------|------------------------------------------------------------------|
| `Company Name`     | Name of the company (text)                                       |
| `Industry`         | Sector, e.g., Technology, Healthcare, Finance, Manufacturing…    |
| `Company Size`     | One of: Micro, Small, Medium, Large, Enterprise                  |
| `LinkedIn URL`     | Full URL to the company’s LinkedIn page                          |
| `Outsourcing Needs`| Comma‑separated list (e.g., `Cybersecurity, Cloud Migration`)   |

*If your CSV has extra columns, they will be ignored – only these five are used.*

---

## 📄 Output Reports

### PDF Report

- **Header** – dark blue banner with report title and your name.
- **Summary** – total companies, industry & size distributions, top 10 outsourcing needs, and industry‑specific top needs.
- **Data table** – all columns, with LinkedIn URLs wrapped to fit the column width.
- **Footer** – visitor counter, generation date, and copyright notice.

#### Visual Elements

- Banner colour: `#2C3E50` (dark blue)  
- Decorative line: `#3498DB` (light blue)  
- The visitor counter is stored in `visitor_count.txt` and increments each time a PDF is generated.

### CSV / Excel

- Contains the exact filtered and sorted data.
- No formatting – ideal for further analysis or import into other tools.

---

## 🤖 AI‑Driven Analysis

The script performs a simple but powerful frequency analysis on the `Outsourcing Needs` column:

1. **Global Top 10** – lists the most commonly mentioned outsourcing services across **all** companies.
2. **Industry‑specific** – for the top 5 industries (by count), it extracts the 3 most frequent needs.

This helps you quickly spot which services are most in demand, both overall and per sector.

*Example output:*
```
--- Most Common Outsourcing Needs (Top 10) ---
  Cybersecurity: 342
  Cloud Migration: 289
  Customer Support: 245
  ...

--- Industry-Specific Outsourcing Insights (AI-driven) ---
  Technology: Top needs -> Cybersecurity (120), Cloud Migration (98), AI Development (67)
  Healthcare: Top needs -> Medical Billing (87), Data Annotation (65), IT Support (54)
```

---

## 🧭 Interactive Walkthrough (Example)

```
$ python company_insight_processor.py

=== Company Insight Processor – Interactive Menu ===

Current working directory: /home/user/projects
Files in this directory:
  company_dataset_10000.csv
  company_insight_processor.py
  ...

Enter your name (for report header): John Doe
Enter input CSV file path (default: company_dataset_10000.csv): 
Enter output report file path (default: report.pdf): tech_report.pdf

Filter options:
  1. Filter by Company Name (substring)
  2. Filter by Industry (exact, case-insensitive)
  3. No filter (show all)
Enter choice (1/2/3): 2
Enter industry name: Technology
Filter by Company Size? (y/n): y
Enter size (e.g., Micro, Small, Medium, Large, Enterprise): Large
Enter column to sort by (default: Company Name): Company Size
Report format (csv/excel/pdf, default: pdf): pdf

... summary and preview ...

Generate report? (y/n): y
PDF report saved to: tech_report.pdf (Visit #12)
```

---

## 🛠️ Customisation

| What to change | Where | How |
|----------------|-------|-----|
| **Header colour** | `generate_pdf()` | Change `colors.HexColor('#2C3E50')` to another hex value. |
| **Decorative line colour** | `generate_pdf()` | Change `colors.HexColor('#3498DB')`. |
| **Column widths** (PDF table) | `col_widths` list in `generate_pdf()` | Adjust the inch values (e.g., `2.0*inch`). |
| **Visitor counter file** | `COUNTER_FILE` variable | Rename `visitor_count.txt` to something else. |
| **Default filenames** | `default_input` and `default_output` in `interactive_mode()` | Change the strings. |
| **Filter options** | The code in `interactive_mode()` | Add new filter types or modify the logic. |

---

## ❓ Troubleshooting

### “The system cannot find the path specified”
- The script prints your current working directory and lists all files – check if your CSV is there.
- If not, provide the **full absolute path** when asked (e.g., `C:\Users\...\data.csv` or `/home/user/data.csv`).

### “reportlab not installed”
- Install it: `pip install reportlab`

### “ModuleNotFoundError: No module named 'pandas'”
- Install pandas: `pip install pandas`

### Excel export fails
- Ensure `openpyxl` is installed: `pip install openpyxl`

### The visitor counter resets
- The counter is stored in `visitor_count.txt`. If you delete this file, it will restart from 1.

---

## 🤝 Contributing

Contributions, bug reports, and feature requests are welcome!  
Please open an issue or submit a pull request on the GitHub repository:

**[akashkarn9486/company-analysis-](https://github.com/akashkarn9486/company-analysis-)**

---

## 📜 License

This project is licensed under the **MIT License** – you are free to use, modify, and distribute it as you wish.

---

**Happy analysing!** 📈
