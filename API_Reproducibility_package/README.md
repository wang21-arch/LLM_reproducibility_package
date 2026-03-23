
# LLM Evaluation Reproducibility Package

This package provides a fully documented, API-based workflow that allows future researchers to reproduce the evaluation procedure described in the manuscript.

The original study was conducted using web-based interfaces of several large language models (LLMs). Because web interfaces evolve rapidly and may become unavailable over time, this package provides a programmatic API workflow that points to the same model families used during the original evaluation.

This package enables reproducibility by providing:

- Source code
- Exact prompt structure
- API-based execution
- Step-by-step instructions
- Model mapping information
- Output file generation rules

No API keys are included in this repository for security reasons.

---

# Repository Structure

The reproducibility package is organized as follows:

01_question_sets/
    Group1_molecules/
    Group2_drugs/
    Group3_comparisons/
    Group4_inference/

run_llm_api_reproducibility_public_safe.py
requirements.txt
.env.example
README.md

The `01_question_sets` directory contains the original prompt files used for the evaluation.

Each prompt is stored as a Word document (.docx).

---

# Model Mapping

The original web-interface evaluation corresponded to the following models:

Web Interface Platform → API Equivalent

ChatGPT → OpenAI API (model: gpt-4o)  
Gemini Advanced → Google Gemini API (model: gemini-2.0-flash)  
Microsoft Copilot → Azure OpenAI API (model equivalent: GPT-4 Turbo deployment)  
Perplexity Pro → Perplexity API (model: Sonar)

This mapping ensures that the API execution corresponds to the same model families used during the original study.

---

# Installation

1. Install Python (version 3.9 or later recommended)

2. Install required packages:

pip install -r requirements.txt

---

# API Key Setup

API keys must NOT be committed to public repositories.

Instead, copy the template file:

.env.example

and rename it to:

.env

Then fill in your personal API keys.

Example:

OPENAI_API_KEY=your_key_here
GEMINI_API_KEY=your_key_here
AZURE_OPENAI_API_KEY=your_key_here
AZURE_OPENAI_ENDPOINT=your_endpoint_here
AZURE_OPENAI_DEPLOYMENT=your_deployment_name
PERPLEXITY_API_KEY=your_key_here

Also configure the input and output directories.

---

# Running the Script

Once the environment variables are configured, run:

python run_llm_api_reproducibility_public_safe.py

The script will:

1. Scan all prompt files
2. Send each prompt to the four LLM APIs
3. Generate four answer files per prompt

---

# Output Structure

For each prompt file:

example.docx

The script will generate:

example_ChatGPT.docx
example_Gemini.docx
example_Copilot.docx
example_Perplexity.docx

Each output file contains the raw response returned by the corresponding model.

---

# Group4 Special Handling

Prompts in Group4 represent inference tasks where the correct drug identity must not be revealed to the model.

The script automatically removes any filename-derived drug identifiers before sending the prompt to the model APIs.

This preserves the intended inference challenge.

---

# Access Dates and Version Information

Original web-interface evaluation:
February 2025 (first week)

API reproducibility package prepared:
2026

Model identifiers:

OpenAI: gpt-4o  
Google Gemini: gemini-2.0-flash  
Azure OpenAI: GPT-4 Turbo deployment  
Perplexity: Sonar

---

# Reproducibility Statement

This package is provided to ensure that the evaluation framework can be reproduced programmatically even if web interfaces evolve or become unavailable in the future.

Researchers can rerun the evaluation using their own API credentials while maintaining the same prompt structure and model families.

---
