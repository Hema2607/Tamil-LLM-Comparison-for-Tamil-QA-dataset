# Tamil Medical Question Answering using Fine-Tuned Language Models

This repository contains the implementation and results of fine-tuning Tamil language models for the task of medical question answering. The work focuses on improving performance in a low-resource language setting by adapting existing large language models through domain-specific fine-tuning.

## Overview

Large language models (LLMs) have shown impressive capabilities across natural language tasks. However, their performance in Tamil, especially for specialized domains like healthcare, is still limited. This project explores the impact of instruction-based fine-tuning on two Tamil-compatible models:

- `abhinand/tamil-llama-7b-instruct-v0.2`
- `abhinand/gemma-2b-it-tamil-v0.1-alpha`

Both models were fine-tuned using a translated medical question answering dataset and evaluated using semantic similarity metrics.

## Dataset

The dataset used for training and evaluation was derived from the MedQuAD English dataset (16,412 Q&A pairs). It was translated into Tamil using the `gopi30/english-to-tamil-stage1` model.

Each sample contains:
- `question_tamil`: A Tamil-translated medical question
- `answer_tamil`: The corresponding Tamil-translated answer

This dataset covers a wide range of topics such as diseases, symptoms, treatments, medications, and diagnostics.

## Fine-Tuning Details

Fine-tuning was conducted on the NIT Puducherry AI server using the following configuration:

- GPU: NVIDIA A100 (80GB)
- Framework: Unsloth (optimized wrapper over HuggingFace)
- Precision: FP16
- Epochs: 5
- Batch Size: 2 (with gradient accumulation)
- Sequence Length: 2048
- Quantization: 4-bit

Identical hyperparameters were used for both models to ensure fair comparison.

## Evaluation

The models were evaluated using BERTScore with Tamil language support (`lang="ta"`), which measures semantic similarity between generated and reference answers.

Key findings:
- Both models showed significant improvement after fine-tuning.
- Tamil-Gemma achieved slightly higher F1 scores.
- Tamil-LLaMA provided more fluent and contextually accurate responses in several cases.

### Qualitative Improvements

Before fine-tuning:
- Responses were often generic or grammatically incorrect.
- Medical context was frequently missing.

After fine-tuning:
- Answers were more relevant and specific.
- Improved fluency and grammar in Tamil.
- Better alignment with medical context.

## Example QA Outputs

| Tamil Question | Tamil-Gemma Answer | Tamil-LLaMA Answer |
|----------------|--------------------|--------------------|
| மொன்ட்ரியல்ஸ் நோய்க்கு என்ன காரணம்? | தெலிலகொபொக்டை பாக்டீரியா... | சுவற்றின் பாதிப்பை உண்டாக்கும் பாக்டீரியா... |
| ஹெனோக் - ஷ்ணுய்ன் பர்பூராவின் அறிகுறிகள் என்ன? | சிவந்த புள்ளிகள், மூட்டு வலி... | வயிற்று வலி, சிறுநீரில் இரத்தம்... |

## Conclusion

Fine-tuning large language models on domain-specific Tamil data significantly improves their performance. Both Tamil-Gemma and Tamil-LLaMA demonstrated better understanding and response generation after training.

These models are now better suited for real-world applications such as:
- Digital healthcare assistants in Tamil
- Rural telemedicine systems
- Patient education tools in regional languages

## Acknowledgements

This work was carried out using the infrastructure at NIT Puducherry. The dataset translation and model support were made possible through open-source tools from HuggingFace and Kaggle.

## Contact

For questions, suggestions, or collaborations, feel free to reach out:

**Name**: Hemalatha M  
**Institution**: Chennai Institute of Technology  
**Email**: [hemalatham2226@gmail.com]  
