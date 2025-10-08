# NLP Framework for Literature Summarisation in Law and Policy

Legal and policy documents are usually long, technical, and tough for the general public to understand. Lawyers and policymakers have the training to make sense of them, but many people representing themselves in court, dealing with regulations, or just trying to stay informed don’t have that background. This creates barriers to justice, learning, and fair decision-making. Automatic summarisation of legal and policy texts is a growing research area that tries to solve this problem. While there’s been good progress, not many projects focus on interactive tools for everyday users.

The objective is to build a chatbot interface powered by summarisation models for literature in law and policy, focusing on empowering people who represent themselves in court or want to understand regulatory frameworks. The chatbot will provide short, easy-to-read summaries tailored to their questions.

*This is a course project for CSE 842 Natural Language Processing at Michigan State University. The project is ongoing.

## Table of Contents
1. [Dataset](#dataset)
2. [Methodology](#methodology)

## Dataset
The [BillSum](https://huggingface.co/datasets/FiscalNote/billsum) dataset is a summarisation of US Congressional and California state bills. The US bills were collected from the Govinfo service provided by the United States Government Publishing Office (GPO) under CC0-1.0 license. The California bills were collected from the 2015-2016 session from the legislature’s website. The [Government report](https://huggingface.co/datasets/ccdv/govreport-summarization?) dataset consists of reports written by government research agencies including Congressional Research Service and U.S. Government Accountability Office.
