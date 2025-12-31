# 🔄 Universal AI Data Ingestion Pipeline

**Project Status:** Internship Capstone Project (Proof of Concept)
**Role:** Web Developer Intern (AI & Data Integration Focus)
**Tech Stack:** Langflow, Python, Vector Database

---

## 📖 Overview

This repository hosts the **"Universal Data Ingestion Router"**, an architectural blueprint designed to solve the **"Garbage In, Garbage Out"** problem in RAG (Retrieval-Augmented Generation) systems.

The system acts as an intelligent middleware that creates a standardized entry point for various file types before vectorization.

---

## 🛑 The Problem

In a real-world enterprise environment, data comes in mixed formats. A generic "Text Loader" fails to capture context specific to each format:
* **📉 Spreadsheets (.xlsx, .csv):** When converted to plain text, row values lose their relationship with column headers. The AI sees numbers but doesn't know what they represent.
* **💻 Source Code (.py, .js):** Standard splitters often strip whitespace, destroying the semantic meaning of indentation-based languages like Python.
* **📄 Documents (.docx, .pdf):** Heading hierarchies are often lost during flat text conversion.

---

## 💡 The Solution: Intelligent Routing Logic

> **Core Workflow:** `workflows/05_universal_data_ingestion_router.json`

This Langflow blueprint implements a logic-based router that:

1.  **Universal Loading:** Accepts any file type via a unified input node.
2.  **MIME-Type Detection:** Automatically identifies the nature of the file (Code vs. Tabular vs. Unstructured).
3.  **Specialized Pre-processing:**
    * **Spreadsheet Route:** Implements "Context Injection" logic—appending column headers to every cell value (e.g., changing `200` to `Weight: 200 kg`).
    * **Code Route:** Uses a code-aware splitter to preserve class/function scope and indentation.
    * **Document Route:** Converts files to Markdown to retain heading structures for better chunking.

---

## 🛠️ Usage

1.  **Download:** Clone this repository or download the JSON file from the `workflows` directory.
2.  **Import:** Open **Langflow** and import `05_universal_data_ingestion_router.json`.
3.  **Configure:**
    * Locate the **Directory / File Loader** node.
    * Update the `Path` to point to your local dataset.
    * Locate the **DataSaver** node and set your desired output destination.

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

*Note: This repository contains architectural blueprints for educational and portfolio purposes. No proprietary client data is included.*
