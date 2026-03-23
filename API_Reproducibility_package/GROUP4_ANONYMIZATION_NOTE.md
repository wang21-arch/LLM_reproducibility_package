
# Group4 Anonymization Note

## Purpose

Group4 prompts are designed as **inference tasks**.  
Each prompt provides partial chemical or pharmacological information about a drug, and the model is asked to infer the identity of the compound.

Because the correct drug identity is embedded in the filename of the prompt document (for dataset organization purposes), a special anonymization step is required before sending the prompt to any LLM API.

If the drug name were included in the prompt text, the inference task would become trivial and would no longer evaluate the model's reasoning ability.

---

## Anonymization Rule

For all files located in:

01_question_sets/Group4_inference/

the evaluation script performs the following procedure:

1. The script reads the prompt text from the Word file.
2. Any drug name derived from the filename is **not included** in the text sent to the LLM.
3. Only the descriptive chemical and pharmacological information is transmitted to the model.

This guarantees that the model receives **only the intended clues**, not the answer.

---

## Example

File name:

warfarin.docx

The model receives a prompt similar to:

"There is a drug with the following properties:
- molecular formula ...
- molecular weight ...
- physical characteristics ...

1. Is this drug chiral?
2. Is it racemic or enantiomerically pure?
3. What is the degree of chirality?
4. Plot the circular dichroism spectrum.
5. What is the identity of this drug?"

The name *warfarin* is **never included in the prompt text** sent to the API.

---

## Importance for Reproducibility

This anonymization step ensures that:

- The evaluation remains a genuine reasoning task.
- The dataset organization does not leak the correct answer.
- Future researchers can reproduce the inference challenge exactly.

The anonymization procedure is implemented directly in the evaluation script.
