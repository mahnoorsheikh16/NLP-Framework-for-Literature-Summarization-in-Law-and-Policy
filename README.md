# NLP Framework for Literature Summarisation in Law and Policy

Legal and policy documents are usually long, technical, and tough for the general public to understand. Lawyers and policymakers have the training to make sense of them, but many people representing themselves in court, dealing with regulations, or just trying to stay informed don’t have that background. This creates barriers to justice, learning, and fair decision-making. Automatic summarisation of legal and policy texts is a growing research area that tries to solve this problem. While there’s been good progress, not many projects focus on interactive tools for everyday users.

The objective is to build a chatbot interface powered by summarisation models for literature in law and policy, focusing on empowering people who represent themselves in court or want to understand regulatory frameworks. The chatbot will provide short, easy-to-read summaries tailored to their questions.

*This is a course project for CSE 842 Natural Language Processing at Michigan State University.

## Table of Contents
1. [Dataset](#dataset)
2. [Methodology](#methodology)

## Dataset
The [BillSum](https://huggingface.co/datasets/FiscalNote/billsum) dataset is a summarisation of US Congressional and California state bills. The US bills were collected from the Govinfo service provided by the United States Government Publishing Office (GPO) under CC0-1.0 license. The California bills were collected from the 2015-2016 session from the legislature’s website. The [Government report](https://huggingface.co/datasets/ccdv/govreport-summarization?) dataset consists of reports written by government research agencies, including the Congressional Research Service and the U.S. Government Accountability Office.

The BillSum dataset consists of three parts: US training bills (18949 observations), US test bills (3269 observations) and California test bills (1237 observations). It contains the following features:

`text`: bill text

`summary`: human-written summary of the bill

`title`: title of the bill

`text_len`: number of chars in text

`sum_len`: number of chars in summary

The GovReport dataset consists of 17517 training, 973 validation and 973 test observations. It contains the following features:

`id`: paper id

`report`: body of the report

`summary`: summary of the report

## Methodology
Preprocessing datasets involves cleaning, tokenising, and chunking long documents. The baseline models are extractive methods, which will be compared to fine-tuned models like PEGASUS or Longformer Encoder-Decoder (LED) for long documents. For chatbot integration, a retrieval layer will get relevant bills/reports based on a user’s query and pass them through the summarisation model to generate concise outputs. Evaluation metrics employed are ROUGE, BLEU, and cosine similarity.

`va_working_area` has everything tested and worked on - it is a rough workspace which helped create embeddings, create functions, make datasets, etc.

`final_work_va` has all the RAG implementation without the messy aspect of the work area. just plug and play

[Resouces to run final_work_va](https://michiganstate-my.sharepoint.com/:f:/g/personal/vennamva_msu_edu/EtaGg0aQghtIiHeymObZ99EBpiZFOMWgQrJw0iWLJLdM6g?e=GIbJK3) - Anyone within MSU can access
