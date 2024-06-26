# Research Article Summarizer 

## Abstract
The primary objective of our initiative is to simplify the lives of students and researchers who frequently encounter an overwhelming volume of lengthy research papers. Natural Language Processing (NLP) and Generative AI are employed to generate concise and informative summaries of the aforementioned articles. In this way, students can promptly determine the relevance of a paper to their task without the need to peruse the entire document. Our methodology includes two primary tactics. The initial step involves identifying the pivotal sentences from the original text and assembling them to create a concise summary. The second task entails a higher level of complexity, as it involves creating novel sentences that concisely summarize the key concepts of the article. Our objective is to enhance the quality of these summaries, surpassing the existing ones.

## Methodology

### 1. Data Collection
The Scisumm dataset utilized in this study was sourced from the ACL Anthology network. This dataset consists of more than 1,000 research publications, each accompanied with summaries provided by experts. This collection comprises 
   - Document XML files that provide a comprehensive description of the structure and content of each publication.
   - Folders containing carefully written summaries.

### 2. Text Preprocessing
The preprocessing steps involve:
   - Leaving unnecessary parts (such as those located above the "Abstract," acknowledgements, and references).
   - Employing spaCy for the purpose of text cleaning and organization.
   - Data conversion into a structured format is a crucial step in the process of model training.

### 3. Tokenization and Train-Test Split
The Pegasus tokenizer was selected because to its high level of proficiency in text summarizing tasks. The data was divided into training and validation sets, with 90% allocated for training and 10% for validation. Tokenization was performed on the data, and the resulting data was arranged into a custom 'SummaryDataset' class using PyTorch.

### 4. Model Training
We explored two primary approaches:
   - **Extractive Summarization using Page Rank Algorithm:** This method selects high-importance sentences based on the PageRank algorithm.
   - **Abstractive Summarization using Pegasus Model:** Involves both pre-trained and fine-tuned Pegasus models for generating new, coherent summaries. Additionally, we experimented with the T5 model for its text-to-text transfer capabilities.

### 5. Output and Evaluation
A comparative analysis was performed on the summaries generated by several models. The performance of our fine-tuned Pegasus model in summarizing a sample climate change document was found to be superior, suggesting its effectiveness in the task of summarizing research articles. The Rouge Scores for various models are presented in the following table:

| Model                           | Rouge_1 | Rouge_2 | Rouge_L |
|---------------------------------|---------|---------|---------|
| Extractive using Page Rank      | 0.18    | 0.10    | 0.12    |
| T5 Transformer                  | 0.50    | 0.38    | 0.41    |
| Pegasus Pre-Trained             | 0.44    | 0.30    | 0.35    |
| Pegasus Fine-Tuned              | 0.57    | 0.46    | 0.50    |

### 6. Model Deployment
The Pegasus model, which had been fine-tuned, was implemented on a website utilizing Flask, providing users with the choice of summary length (short, medium, lengthy). The research paper is entered by users, who thereafter receive a processed summary.

### 7. Possible Improvements and Considerations
Potential improvements encompass comparing performance against alternative summarization algorithms, conducting iterative training using fresh data, and tackling ethical concerns such as bias.

## Conclusion
The objective of this project is to create a tool that can effectively summarize text and capture the core information of intricate research papers in a brief manner. This tool will tackle the difficulties associated with language processing and the individual particulars of different domains.

## Reference
- [SciSummNet - Scientific Article Summarization Dataset](https://cs.stanford.edu/~myasu/projects/scisumm_net/)
- [Finetuning Pegasus model - Hugging Face Discussion](https://discuss.huggingface.co/t/fine-tuning-pegasus/1433)
