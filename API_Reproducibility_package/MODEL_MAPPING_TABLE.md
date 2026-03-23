
# Model Mapping Table

This document specifies the mapping between the web-interface models used in the original evaluation and the API-accessible models used in the reproducibility workflow.

The original study relied on commercial web interfaces. Because web interfaces evolve and may be deprecated, this reproducibility package provides API-based access to the same model families.

## Mapping Overview

| Original Platform | Interface Used in Study | API Provider | API Model Identifier | Notes |
|------------------|------------------------|--------------|----------------------|------|
| ChatGPT | ChatGPT web interface | OpenAI API | gpt-4o | Corresponds to the GPT‑4o model family used during the original evaluation period |
| Gemini Advanced | Google Gemini web interface | Google Gemini API | gemini-2.0-flash | API-accessible model within the Gemini 2.x family |
| Microsoft Copilot | Copilot web interface | Azure OpenAI API | GPT‑4 Turbo deployment | Azure deployment corresponding to the Copilot backend model family |
| Perplexity Pro | Perplexity web interface | Perplexity API | Sonar | API-accessible Sonar model used for retrieval-augmented generation |

## Rationale

The purpose of this mapping is to ensure that the reproducibility workflow accesses the same model families used in the original evaluation.

Because web interfaces may change or be deprecated, API endpoints provide a stable mechanism for programmatic execution.

## Important Note

The API models used in this workflow correspond to the same model families available during the original evaluation period. However, API providers may update backend implementations over time. Therefore, researchers should document:

- Execution date
- Model identifier
- Provider API version

when reproducing the evaluation.
