# Text-Summarization-Using-Transformers-and-Pretrained-Models
## Introduction

This report outlines the comparison of three pretrained text summarization models: BART, T5, and Pegasus. We utilized the SAMSum dataset, which contains messenger-like conversations along with their human-written summaries. The primary goal was to evaluate and compare the summarization performance of these models using the ROUGE, BLEU, METEOR, and BERTScore evaluation metrics.

## Methodology

### Setup and Installation

1. **Libraries Installation**: We installed essential libraries including `transformers`, `datasets`, `py7zr`, and `rouge-score` to facilitate model loading, dataset handling, and evaluation.
2. **GPU Setup**: We ensured that our environment had access to a GPU to speed up the computations.

### Loading Models and Dataset

1. **Dataset Loading**: We loaded the SAMSum dataset using the `datasets` library. The validation split, containing 818 samples, was used for evaluation.
2. **Model and Tokenizer Loading**: We loaded the pretrained BART, T5, and Pegasus models along with their corresponding tokenizers from the Hugging Face model hub.

### Summarization Function

We defined a function to generate summaries using the loaded models. This function included parameters such as `max_length`, `min_length`, and `num_beams` to control the beam search process during text generation. Beam search helps improve the quality of the generated summaries by considering multiple possible sequences and selecting the best one based on cumulative probability.

### Evaluation Process

1. **Summary Generation**: Using the defined summarization function, we generated summaries for each dialogue in the validation set with each of the three models (BART, T5, and Pegasus).
2. **Performance Comparison**: We compared the generated summaries against the reference summaries using the ROUGE, BLEU, METEOR, and BERTScore metrics. These metrics measure different aspects of the generated summaries' quality:
    - **ROUGE**: Measures the overlap of unigrams, bigrams, and longest common subsequences between the generated summary and the reference summary.
    - **BLEU**: Measures the precision of n-grams in the generated summary compared to the reference summary.
    - **METEOR**: Combines precision and recall of n-grams, considering synonymy and paraphrasing.
    - **BERTScore**: Uses BERT embeddings to compare the semantic similarity of the generated summary and the reference summary.

## Results

### ROUGE Scores

The average ROUGE scores across the validation set were as follows:

- **BART**:
  - ROUGE-1: 0.3556
  - ROUGE-2: 0.1260
  - ROUGE-L: 0.2768

- **T5**:
  - ROUGE-1: 0.2734
  - ROUGE-2: 0.0843
  - ROUGE-L: 0.2157

- **Pegasus**:
  - ROUGE-1: 0.3212
  - ROUGE-2: 0.1038
  - ROUGE-L: 0.2489

### BLEU, METEOR, and BERTScore

- **BART**:
  - BLEU: 0.0610
  - METEOR: 0.3307
  - BERTScore: 0.8778

- **T5**:
  - BLEU: 0.0403
  - METEOR: 0.2493
  - BERTScore: 0.8590

- **Pegasus**:
  - BLEU: 0.0501
  - METEOR: 0.2642
  - BERTScore: 0.8621

### Visualization

We created bar plots to visualize the ROUGE, BLEU, METEOR, and BERTScore metrics for each model, clearly showing BART's superior performance, followed by Pegasus and then T5.

## Analysis

The results indicate that BART consistently outperforms T5 and Pegasus across all evaluation metrics, demonstrating its robustness in generating high-quality summaries.

- **BLEU Scores**: BART achieved the highest BLEU score, which reflects its superior ability to produce precise n-grams in comparison to the reference summaries. T5 had the lowest BLEU score, indicating less precise n-gram matches.
- **METEOR Scores**: BART also led in METEOR scores, which consider both precision and recall, along with synonymy and paraphrasing. This suggests BART's summaries are not only precise but also recall a significant portion of the reference summary content.
- **BERTScores**: BERTScore evaluates semantic similarity using BERT embeddings. Again, BART achieved the highest score, indicating that its summaries are closest in meaning to the reference summaries. Pegasus scored slightly better than T5, placing it between BART and T5 in terms of semantic similarity.

## Conclusion

The comparative analysis showed that BART is the best model for text summarization among the three, based on the ROUGE, BLEU, METEOR, and BERTScore metrics. T5 showed the least effectiveness, while Pegasus stood as an intermediate performer. Future work may include fine-tuning these models on the SAMSum dataset to potentially improve their summarization performance further.
