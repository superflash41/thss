+++
title = "LiW24 - Combining Induction and Transduction for Abstract Reasoning"
date = '2025-06-01'
toc = true
math = true
tags = ["LiW24", "intelligence", "ARC-AGI"]
hideBackToTop = true
pdf = "https://arxiv.org/pdf/2411.02272.pdf"
draft = false
+++

---

## Overview

This paper explores a novel approach to abstract reasoning in the Abstraction and Reasoning Corpus (ARC) by **combining inductive and transductive paradigms**. The authors introduce a pipeline that leverages both paradigms using large language models (LLMs) and a large-scale synthetic data generation process.

The key contributions include:
- A method for **generating synthetic ARC-style problems** from a small set of human-written seed programs.
- A dual approach that combines induction (**program synthesis**) and transduction (direct prediction) to solve ARC tasks.
- A resulting performance of **56.75%** on the **validation set**, and a spot on the top of the ARC Prize leaderboard.

---

## 1 Core Idea

Induction involves inferring an explicit **latent function** (represented as *Python* code) that explains the observed examples. This involves **synthesizing programs** that fit the training examples and then using them to make predictions on new inputs.

Transduction is just about **directly predicting outputs** for new test inputs by leveraging neural networks trained on many examples.

The authors demonstrate that induction and transduction are highly complementary: while induction is better for tasks requiring precise computation and symbolic composition, transduction excels in handling perceptual and fuzzier tasks. Importantly, these paradigms are **combined in an ensemble**, where induction is attempted first, and transduction serves as a fallback if no consistent function is found.

## 2 Synthetic Data Generation Pipeline

A key innovation of the paper is the pipeline for generating a large synthetic dataset. It begins with a set of 100-160 human-written *seed programs* that solve ARC tasks. Each seed consists of:
1. A natural language description of the task.
2. A Python function (`transform_grid`) that implements the transformation.
3. An `input_generator` function to produce new example inputs.

To scale up, the authors use *Retrieval Augmented Generation* (RAG) to **remix and mutate these seeds**, creating thousands of synthetic *ARC-style* problems. This synthetic data generation is crucial for *fine-tuning* the neural models, providing a massive dataset beyond the original.

## 3 Neural Models and Training

The models used are based on *Llama3.1-8B-instruct*, which is particularly well-suited for tasks involving code. Inductive and transductive models share the same architecture and are trained with meta-learning objectives: induction maximizes the likelihood of finding the correct function, while transduction maximizes the likelihood of predicting the correct output.

The synthetic dataset drives the models' training, with evidence showing that increasing synthetic data size leads to improved performance, while simply increasing the number of seeds (human effort) yields diminishing returns.

## 4 Evaluation and Results

Experiments reveal that:
- Induction and transduction models solve different subsets of ARC tasks.
- Performance scales better with more compute (sampling budget for induction) than with more manual data.
- Test-time sampling for induction improves solve rates by exploring many candidate programs and filtering those consistent with training examples.

The final ensemble system, called BARC, achieves 56.75% accuracy on ARC’s validation set—comparable to average human performance and the best open-source result at the time. The approach outperforms purely transductive or inductive methods, illustrating the value of combining both.

## 5 Broader Implications and Relation to AGI

The work positions itself within the debate on general intelligence (AGI) by showcasing how combining symbolic (induction) and subsymbolic (transduction) reasoning can solve complex, few-shot learning tasks. This dual-process strategy is analogous to human cognitive processes and suggests pathways for extending such hybrid reasoning to other domains like web scraping, robotic planning, and scientific modeling.

## 6 Implementation Details and Scaling

The authors highlight that while they rely on synthetic data, the core "manual" data—human-written seeds—remains modest, suggesting a sample-efficient methodology. They acknowledge that the approach does not learn new concepts autonomously from scratch but rather amplifies human-encoded knowledge through LLM remixing and fine-tuning.

The final models do not incorporate test-time training for induction, focusing on sampling diversity instead, while transduction models do use test-time training and data augmentation to further improve accuracy.

## 7 Conclusion

The paper’s methodology effectively bridges neural and symbolic approaches to abstract reasoning, demonstrating strong performance and laying the groundwork for future research into hybrid, flexible reasoning systems. By showing that induction and transduction are not only complementary but also robust to changes in model initialization and training data, it underscores the potential of combining explicit program synthesis with direct prediction in AI systems.









