
# Step-by-Step Instructions for Reproducing the LLM Evaluation

This document provides a detailed step-by-step guide to reproduce the evaluation workflow using API-based access to the same model families used in the original study.

---

## Step 1: Install Python

Ensure that Python 3.9 or later is installed.

Check installation:

python --version

---

## Step 2: Install Required Libraries

Navigate to the directory containing this reproducibility package and run:

pip install -r requirements.txt

This will install all required dependencies.

---

## Step 3: Obtain API Keys

You will need API credentials for the following services:

OpenAI  
Google Gemini  
Azure OpenAI (for the Copilot condition)  
Perplexity

Follow the official provider documentation to obtain keys.

---

## Step 4: Configure Environment Variables

Copy the template configuration file:

.env.example

Rename it to:

.env

Then replace placeholder values with your own credentials.

Example:

OPENAI_API_KEY=your_key_here
GEMINI_API_KEY=your_key_here
AZURE_OPENAI_API_KEY=your_key_here
AZURE_OPENAI_ENDPOINT=your_endpoint_here
AZURE_OPENAI_DEPLOYMENT=your_deployment_name
PERPLEXITY_API_KEY=your_key_here

---

## Step 5: Configure Input and Output Directories

In the `.env` file, specify:

INPUT_ROOT=path_to_01_question_sets
OUTPUT_ROOT=path_to_output_directory

The input directory should contain the four question groups:

Group1_molecules  
Group2_drugs  
Group3_comparisons  
Group4_inference

---

## Step 6: Run the Evaluation Script

Execute the main script:

python run_llm_api_reproducibility_public_safe.py

The script will automatically:

1. Load all question files
2. Send prompts to the four APIs
3. Generate model responses
4. Save responses as Word files

---

## Step 7: Inspect Output Files

For each input file:

example.docx

The script will generate:

example_ChatGPT.docx
example_Gemini.docx
example_Copilot.docx
example_Perplexity.docx

Each file contains the raw response from the corresponding model.

---

## Step 8: Special Handling of Group4

Group4 prompts contain inference tasks where the correct drug identity must remain hidden from the model.

The script automatically removes drug identifiers derived from filenames before sending prompts to the APIs.

---

## Step 9: Verify Reproducibility

Researchers can verify reproducibility by:

1. Running the script with their own API credentials
2. Comparing outputs with the provided raw responses
3. Confirming prompt structures match the original evaluation.

---

## Step 10: Document Access Dates

Record the execution date and model identifiers when rerunning the evaluation.

This ensures reproducibility across future model versions.
