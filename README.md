# Homophobia-Transphobia-Detection

This repository contains the code for the shared task on homophobia/transphobia detection at the second LT-EDI Workshop @ACL 2022. The paper can be accessed here: [bitsa_nlp@LT-EDI-ACL2022: Leveraging Pretrained Language Models for Detecting Homophobia and Transphobia in Social Media Comments](https://arxiv.org/abs/2203.14267)

## How to cite us?
If you use this code or the fine-tuned models, please cite the following paper:

```
@inproceedings{bhandari-goyal-2022-bitsa,
    title = "bitsa{\_}nlp@{LT}-{EDI}-{ACL}2022: Leveraging Pretrained Language Models for Detecting Homophobia and Transphobia in Social Media Comments",
    author = "Bhandari, Vitthal  and Goyal, Poonam",
    booktitle = "Proceedings of the Second Workshop on Language Technology for Equality, Diversity and Inclusion",
    month = may,
    year = "2022",
    address = "Dublin, Ireland",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2022.ltedi-1.18",
    pages = "149--154",
    abstract = "Online social networks are ubiquitous and user-friendly. Nevertheless, it is vital to detect and moderate offensive content to maintain decency and empathy. However, mining social media texts is a complex task since users don{'}t adhere to any fixed patterns. Comments can be written in any combination of languages and many of them may be low-resource.In this paper, we present our system for the LT-EDI shared task on detecting homophobia and transphobia in social media comments. We experiment with a number of monolingual and multilingual transformer based models such as mBERT along with a data augmentation technique for tackling class imbalance. Such pretrained large models have recently shown tremendous success on a variety of benchmark tasks in natural language processing. We observe their performance on a carefully annotated, real life dataset of YouTube comments in English as well as Tamil.Our submission achieved ranks 9, 6 and 3 with a macro-averaged F1-score of 0.42, 0.64 and 0.58 in the English, Tamil and Tamil-English subtasks respectively. The code for the system has been open sourced.",
}
```

Here is the competition codalab webpage: [https://competitions.codalab.org/competitions/36394](https://competitions.codalab.org/competitions/36394)

## Introduction

We have experimented with a variety of mono-lingual and multi-lingual transformer models along with data augmentation techniques for detection of homophobic/transphobic content among topical youtube comments in 3 settings: English, Tamil and code-mixed Tanglish language.

You can view the split of the dataset in Table 1.

![image](https://user-images.githubusercontent.com/51982356/163250513-48f099e4-fc68-4a36-807a-c7f89dcb4d7f.png)

## Preprocessing and Data Augmentation

Two different preprocessing methods were adopted. First, punctuation symbols were removed, since social media comments are highly informal and tend to contain large number of punctuation symbols which may dilute the system performance. In addition, de-emojification was carried out to replace emojis in the text with corresponding English expressions using the Python emoji package. Table 2 displays a sample de-emojification example.

![image](https://user-images.githubusercontent.com/51982356/163255747-35dbcccb-5492-40ed-9eac-e01a171cabbe.png)

For this task (in English), Surface Form Alteration as exhibited by Easy Data Augmentation (EDA) was utilized (Wei and Zou, 2019).

![image](https://user-images.githubusercontent.com/51982356/163255889-b72cb0ac-7430-4089-be4b-6159d956ee1f.png)

## Results

### English

![image](https://user-images.githubusercontent.com/51982356/163254920-b1e8b7bd-7f2e-4e60-a5be-245c94ccfb3f.png)

![image](https://user-images.githubusercontent.com/51982356/163254983-152b986e-adf2-4aa0-ad34-13f030d6e565.png)

### Tamil

![image](https://user-images.githubusercontent.com/51982356/163255020-946302b8-f639-418b-91e7-50e0539f88dd.png)

![image](https://user-images.githubusercontent.com/51982356/163255062-72fad5eb-f012-4f40-a6d7-50b060478be2.png)


### Code-mixed

![image](https://user-images.githubusercontent.com/51982356/163255220-0715bc4d-2659-4342-b545-b65c80764a77.png)

![image](https://user-images.githubusercontent.com/51982356/163255287-416b1482-5c34-44e1-8525-67abb157e4bc.png)


## Reproducing the baselines

Reproducing the baselines has been made extremely convenient with the help of self-contained executable files.

You may want to start by running the [Data_Ingestion.ipynb](https://github.com/vitthal-bhandari/Homophobia-Transphobia-Detection/blob/master/Baselines/Data_Ingestion.ipynb) script to generate corresponding preprocessed and augmented files from the original dataset. Remember to run the script in the same directory as the dataset.

Once you have ingested the data and generated suitable csv files from it, you can use them as inputs to any of the three baseline scripts in the [Baselines](https://github.com/vitthal-bhandari/Homophobia-Transphobia-Detection/tree/master/Baselines) folder.

the scripts should run without fail and provide you with the baseline for any track. Keep in mind that the final results may differ by an acceptable margin since no seed variable was used to ground reproducibility.

## Ablation study

We first evaluate the performance of a majority classifier on the dataset.

![image](https://user-images.githubusercontent.com/51982356/163253592-e4655629-99b1-4321-b634-f4fa6ea4ad64.png)

We also conduct an extensive ablation study and present the results in Table 12.

![image](https://user-images.githubusercontent.com/51982356/163252217-07a81eb7-0fae-43b6-b732-c9dd8f06bdae.png)

We observed that the effect of preprocessing was largely dependent on the **choice of language setting**. This makes sense considering the difference in underlying language constructs. Tamil, for instance, does not make use of standard English-based punctuation marks. On the other hand, we conclude that the choice of an effective DA techniqe depends on the **underlying task and the data source**. Social media data often lacks linguistic purism and hence, token perturbations such as those introduced by EDA did not help.

The [Ablations](https://github.com/vitthal-bhandari/Homophobia-Transphobia-Detection/tree/master/Ablations) directory is self contained in that the input files needed to run [Ablation_studies.ipynb](https://github.com/vitthal-bhandari/Homophobia-Transphobia-Detection/blob/master/Ablations/Ablation_studies.ipynb) can be obtained by executing the [Data_Ingestion.ipynb](https://github.com/vitthal-bhandari/Homophobia-Transphobia-Detection/blob/master/Ablations/Data_Ingestion.ipynb) script in the same directory. Remember to run the ingestion script in the same folder as the original dataset.


Please cite the following paper when using the dataset:

```
 @article{chakravarthi2021dataset,
  title={Dataset for Identification of Homophobia and Transophobia in Multilingual YouTube Comments},
  author={Chakravarthi, Bharathi Raja and Priyadharshini, Ruba and Ponnusamy, Rahul and Kumaresan, Prasanna Kumar and Sampath, Kayalvizhi and Thenmozhi, Durairaj and Thangasamy, Sathiyaraj and Nallathambi, Rajendran and McCrae, John Phillip},
  journal={arXiv preprint arXiv:2109.00227},
  year={2021}
 }
```
