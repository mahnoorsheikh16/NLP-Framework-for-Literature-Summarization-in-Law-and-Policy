# NLP Framework for Literature Summarisation in Law and Policy

Legal and policy documents are usually long, technical, and tough for the general public to understand. Lawyers and policymakers have the training to make sense of them, but many people representing themselves in court, dealing with regulations, or just trying to stay informed don’t have that background. This creates barriers to justice, learning, and fair decision-making. Automatic summarisation of legal and policy texts is a growing research area that tries to solve this problem. While there’s been good progress, not many projects focus on interactive tools for everyday users.

The objective is to build a chatbot interface powered by summarisation models for literature in law and policy, focusing on empowering people who represent themselves in court or want to understand regulatory frameworks. The chatbot will provide short, easy-to-read summaries tailored to their questions.

*This is a course project for CSE 842 Natural Language Processing at Michigan State University.

## Table of Contents
1. [Dataset](#dataset)
2. [Summarisation Pipeline](#summarisation-pipeline)
3. [Question Answering (QA) & Retrieval (RAG-style)](#question-answering-qa-retrieval-rag-style)
4. [Notebook Structure](#notebook-structure)

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

## Summarisation Pipeline
The summarisation component focuses on generating concise, structured summaries of long legal and policy documents such as U.S. bills and government reports. Preprocessing involves extensive cleaning to remove boilerplate artifacts, followed by sentence tokenisation and token-aware chunking to handle documents exceeding standard transformer limits.

As a baseline, an extractive TF-IDF cosine similarity approach is implemented to identify central sentences, serving as a reproducible performance floor. This is compared against fine-tuned abstractive transformer models, including DistilBART and long-document architectures such as Longformer Encoder-Decoder (LED), which are adapted for legal text using hierarchical chunk-level summarisation.

Evaluation is conducted using ROUGE-1, ROUGE-2, and ROUGE-L metrics, demonstrating substantial improvements of the fine-tuned models over extractive baselines. The summarisation pipeline is also designed to support downstream chatbot integration, where retrieved documents or sections can be summarised on demand while preserving legal context and structure.

## Question Answering (QA) & Retrieval (RAG-style)
The QA component is designed to enable targeted information access over legal and policy documents through retrieval-based methods. Given a user query, documents are first segmented into semantically meaningful chunks, with dataset-specific tokenisers applied (e.g., T5 for BillSum and LED for GovReport). SentenceTransformer embeddings are computed for all chunks, and cosine similarity is used to retrieve the most relevant sections for a given query.

Rather than relying on fully generative answers, the system emphasises factual reliability by retrieving the most relevant summarised content. A lightweight QA model is applied to rank and select the best supporting chunk, ensuring responses remain grounded in the source text. This retrieval-centric design enables fast, stable, and reproducible outputs while remaining computationally feasible in constrained environments.

This approach demonstrates how summarisation can act as a supporting layer for legal QA.

## Notebook Structure
`SummarisationModel.ipynb` focuses exclusively on the summarisation pipeline.

`va_working_area` has everything tested and worked on. It serves as an experimental workspace, which contains exploratory work used to create embeddings, test retrieval strategies, prototype functions, construct intermediate datasets, and validate modeling choices.

`final_work_va` has the clean, finalised implementation of the QA retrieval pipeline without the messy aspect of the work area. Just plug and play.

[Resouces to run final_work_va](https://michiganstate-my.sharepoint.com/:f:/g/personal/vennamva_msu_edu/EtaGg0aQghtIiHeymObZ99EBpiZFOMWgQrJw0iWLJLdM6g?e=GIbJK3) : Anyone within MSU can access.
