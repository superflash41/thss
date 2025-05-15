+++
title = "Cho19 - On the Measure of Intelligence"
date = '2025-05-14'
toc = true
math = true
tags = ["Cho19", "intelligence", "ARC-AGI"]
hideBackToTop = true
pdf = "https://arxiv.org/pdf/1901.11150.pdf"
draft = false
+++

---

## Overview

- The main goal of the AI field since its inception has been to create human-like artificial 
intelligence. However, Chollet argues that this goal has not been possible to achieve given that there
is no clear definition of intelligence, neither a standard way to measure it.

- In this context, he proposes a **formal definition of intelligence**, and a set of guidelines on **how
a general AI benchmark should look like**. Following this, he introduces the *Abstraction and Reasoning
Corpus* (ARC) as a tool to evaluate artificial *fluid* intelligence.

---

## 1 Context and History

### 1.1 Need for an actionable definition and measure of intelligence

- We have been able to engineer systems that excel a specific tasks, but they still have limitations
regarding their capacity to work with little data, or on repurposing themselves to deal with novel
situations for which they were not trained.

- The problem behind this is that we do not have a clear definition of what intelligence is, even when
the field has already some 70 years of history. With no clear definition, there is no a goal to pursue.
Even worse, there is no a established standard way to measure it.

- Then, it becomes obvious that we need two things:
    - A clear definition of intelligence that is actionable, explanatory and **measurable**.
    - A standard and reliable way to measure it.

- Some guilt resides on the AI community itself, as it has constantly been ignoring the efforts of
establishing comprehensive and formal definitions and evaluation methods. To Chollet, this is a
mistake. In this paper, he will point out the implicit assumptions on which the field has been working,
and attempt to correct most of them.

### 1.2 Defining intelligence: two divergent visions

- We must start then analyzing the current state of the field. In the context of AI research, Legg and
Hutter (2007) summarized 70 definitions into: "Intelligence measures an agent's ability to achieve
goals in a wide range of environments".

- From this definition, we can extract two main components:
    - *to achieve goals*: task-specific skill
    - *in a wide range of environments*: capability of generalization and adaptation

- Implicit in the second one, is the fact that an agent needs to be able to learn to handle new tasks
(skill acquisition) for it to truly achieve generality.

- The two components of that definition, map themselves to the two main views of the human's mind
nature: one view considers the mind as a static assembly of special-purpose mechanisms developed
through evolution, and set to only learn what it was programmed to, and another view in which
the mind is a blank slate (Tabula Rasa) capable of turning experience into knowledge and skills.

- We must then start analyzing these perspectives before we can formulate our own definition.

![perspectives](/images/perspectives.png#small "Two perspectives")

#### 1.2.1 Intelligence as a collection

- Originated in Darwin (1859), this view considers the mind as a collection of special-purpose
adaptations developed by humans to solve specific problems they faced during evolution.

- To the AI community, this view srved as a base for the development of their own definition














![just-that](/images/just-that.png#small "Just that")