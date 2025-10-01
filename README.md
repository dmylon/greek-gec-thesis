# Development of a Grammatical Error Correction Model for the Greek Language

## Description

This repository presents the development of a Grammatical Error Correction (GEC) model for the Greek language. The project explores how advanced neural architectures, and particularly the Transformer family of models (T5, BART, etc.), can be adapted to the unique challenges of Modern Greek, a language for which digital linguistic tools are still limited compared to English. This project was developed for my Thesis which can be accessed in this [link](https://ikee.lib.auth.gr/record/356533/files/Dimitrios_Mylonas.pdf).

The system corrects spelling, grammatical, and syntactic errors in written Greek by framing the task as a translation problem: the “source” language is erroneous Greek text, while the “target” is its corrected version.

## Project Overview

The motivation for this work stems from the growing digitization of communication. Emails, academic texts, and social media posts are all expected to be free of grammatical and syntactical mistakes. For Greek speakers and learners, however, automated tools remain scarce.  

This thesis tackles that problem by:  
- Collecting and curating existing datasets of erroneous–corrected Greek sentences.  
- Creating a **synthetic dataset of 60,000 examples** with **43 error types**, generated from Wikipedia texts.  
- Training and fine-tuning a Transformer-based neural model on these resources.  
- Evaluating the model’s performance with standard NLP metrics, such as **BLEU** and **Normalized Levenshtein Similarity**.  

By combining **real learner data** with **artificially generated errors**, the project demonstrates that robust grammatical correction is achievable even in a **low-resource language setting**.

## Methodology

The project unfolds in several stages. First, publicly available datasets such as the **Greek Native Corpus (GNC)** and the **Greek Learner Corpus Corrections (GLC2)** were used as a baseline. These corpora consist of sentences written by native and non-native speakers, together with their expert corrections.  

Since the amount of annotated Greek data is limited, a major contribution of this work is the creation of a **Synthetic Dataset**. Using texts from the Greek Wikipedia, 43 categories of frequent errors were systematically introduced, ranging from article–noun agreement mistakes to incorrect prepositions and verb conjugations. Each erroneous sentence was paired with its corrected counterpart, resulting in a balanced dataset of **60,000 pairs**.  

The model training followed a **supervised learning approach**, where erroneous sentences served as input and corrected sentences as output. The architecture leveraged **mT5/GreekT5**, pretrained multilingual/Greek-specific models fine-tuned with these datasets. Training optimization employed the **AdamW algorithm** with learning rate scheduling, while tokenization relied on **SentencePiece** for robust handling of Greek morphology.  

Evaluation was carried out with both **quantitative metrics** (BLEU, Levenshtein similarity) and **qualitative analysis**, showing that the system can effectively correct a wide variety of grammatical and syntactic errors.

## Repository Contents

The files included in this repository are the following:

- **greek_basic_training.ipynb**: This notebooks contains the code for finetuning the **Greek-T5-GreekSum** model introduced in [Giarelis et al., 2023](https://arxiv.org/pdf/2311.07767). The finetuning process involves two already existing datasets for the Grammatical Error Correction Task in Greek Language, namely GNC and GLC2 introduced in [Korre et al., 2021](https://aclanthology.org/2021.ranlp-1.81.pdf) and [Korre and Pavlopoulos, 2022](https://aclanthology.org/2022.lrec-1.532.pdf) respectively. The public datasets can be found in this [repo](https://github.com/katkorre/elerrant).

- **greek_dataset_production.ipynb**: This notebook contains the code for producing a Synthetic Grammatical Error Correction Dataset in Greek along with some statistics associated with the dataset. The created dataset contains synthetic errors using Greek Wikipedia texts which can be found in this [link](https://huggingface.co/datasets/wikimedia/wikipedia).

- **greek_synthetic_training.ipynb**: This notebook contains the code for finetuning a model in the new Synthetic dataset created in the previously mentioned notebook.

- **datasets**: A folder containing all necessary synthetic dataset files.
    - **train_dataset_60k.csv**: Training split of the Synthetic Dataset consisting of 48k examples.
    - **validation_dataset_60k.csv**: Validation split of the Synthetic Dataset consisting of 6k examples.
    - **test_dataset_60k.csv**: Testing split of the Synthetic Dataset consisting of 6k examples.
    - **error_stats.csv**: A complementary file containing information about each error.

## Results

The results highlight the importance of combining authentic and synthetic data. The baseline training on GNC and GLC2 provided reasonable corrections, but the addition of the synthetic dataset led to significant improvements in both BLEU and Levenshtein scores.  

The system showed strong performance in correcting frequent categories such as **agreement errors** (noun–article, subject–verb), **verb tense inconsistencies**, and **prepositional mistakes**. More complex phenomena, such as stylistic or contextual errors, remain challenging, but overall the model provides a solid foundation for grammar correction in Greek.

## Example of Usage

- **Input (erroneous):**  
«Κατά των Β’ παγκόσμιο Πόλεμο βομβαρδίστηκε επανειλημμενα . Ωσόσο , σα Μεταπολεμικά χρόνια ει πολη ανηκοδομήθηκε , καθώς η εώρα απεκτησε πλωυτοπαραγωγικές πηγες από την εκσόρυξη κητασμάτων πετρελαίοι .»
  
- **Corrected:**  
  «Κατά τον Β’ Παγκόσμιο Πόλεμο βομβαρδίστηκε επανειλημμένα. Ωστόσο, στα μεταπολεμικά χρόνια η πόλη ανοικοδομήθηκε, καθώς η χώρα απέκτησε πλουτοπαραγωγικές πηγές από την εξόρυξη κοιτασμάτων πετρελαίου.»

## References
- [Korre & Pavlopoulos](https://aclanthology.org/2022.lrec-1.532.pdf), *ELERRANT: Automatic Grammatical Error Type Classification for Greek* (RANLP 2021).  
- [Evdaimon et al.](https://arxiv.org/pdf/2304.00869), *GreekBART: The First Pretrained Greek Sequence-to-Sequence Model* (2023).  
- [Giarelis et al.](https://arxiv.org/pdf/2311.07767), *GreekT5: A Series of Greek Sequence-to-Sequence Models* (2023).  
  
  

