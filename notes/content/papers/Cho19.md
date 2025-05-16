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

- To the AI community, this view served as a base for the development of their definition of
intelligence. They considered it as a set fo static program-like routines, which relied on logical operators for problem solving, and a database-like memory for storing knowledge.

- It became popular then in the field that the "problem of intelligence" would be solved if er could
better encode human skills into formal rules, and knowledge into databases. This resulted on
evaluation protocols basing themselves on performance on specific tasks.

- As pointed out by Hernánder-Orallo (2017), this view resulted into a paradox: "the AI field
became successful in developing artificial system that could perform very well on specific tasks
without featuring intelligence at all". This trend is still present today.

#### 1.2.2 Intelligence as a general learning ability

- The other view of intelligence is based on the idea that intelligence lies into the ability to
acquire new skills through learning. This ability could then be applied to a wide range of unseen
problems, or even any problem at all.

- This view of intelligence is aligned with the cognitive sciences idea of the mind as a blank slate,
a flexible, adaptable, highly general process that could turn experience into behavior, knowledge and
skills.

- Although this idea of generality through learning was at the core of AI at the birth of the field,
it wasn't until the 80s that it started to be taken seriously with the revolution of deep learning.
During this peak, was that many researchers started to conceptualize the mind as a "randomly
initialized neural network" that starts blank and derives skills from "training data". We see the
world through the lens of the tools we are most familiar with.

- Today, it has become obvious that both perspectives, either a collection of special-purpose
programs or a general-purpose Tabula Rasa, are incorrect.

### 1.3 AI evaluation: from measuring skills to measuring broad abilities

- Not only the definition is concerning, but also the evaluation methods. In both of the seen
perspectives, there has not been established a single formal way to do skill-based evaluation.

#### 1.3.1 Skill-based, narrow AI evaluation

- Historically, to evaluate systems we have:
    - Human review: Human judges observe the input-output pairs and score them. Howver, this method
    is expensive, impossible to automate or scale, and is subjective.
    - White-box analysis: The system is analyzed from the inside, and its useful to evaluate if
    a it is working as intended.
    - Peer confrontation: Two systems compete agains each other to find the best one.
    - Benchmarking: Having a system produce outputs for which "test sets" have been defined,
    and desired outputs are known.

- In particular, benchmarks are considered to be the best tools for evaluation given that they are
reproducible, fair, scalable, easy to set up (most times), and flexible enough to be applicable to
a wide range of possible tasks. This is why is the preferred method in the field.

- However, benchmarks include a little problem. There exists the posibility that the result systems
focus on exceling at a particular metric or task, making the solution overly optimized for that
task, and not generalizable to others, which would not align with the sort of human intelligence that
the field of AI is set to build.

- As humans, being very good at a specific task is considered to be a prove of intelligence, because
it demonstrates the implicit ability we must have had in first place to learn how to do that task.
Furthermore, it suggests that we could learn to extend this ability to other tasks or domains.

- On machines this is not the case. Machines being excelent at specific tasks does not prove them
to be intelligent. And this results in the same paradox as before: "artificial systems can solve
super hard problems without being intelligent at all".

- This confusion can arise from the fact that in humans the process of intelligence (the ability to
learn many skills) and the artifact produced by this process (the good results on a particular task)
are intertwined. In other words, for humans being good at one task is enough to prove intelligence,
while for machines it is just that: being good at one task.

![just-that](/images/just-that.png#small "Just that")

- The problem then with the AI field has not been that AI systems have been measured by their
performance on specific tasks. The problem has been that this results have been considered as a
prove of success in a field whose main goal was to develop systems that can show autonomy and dynamiclly need to adapt to changes like humans do.

- We must then correct the way this success is measured. And for that we must focus on the
particular aspects current problems in the field exhibit: the need of flexibility and robustness.
Moreover, it has become evident that we need to move beyond skill-based evaluation, to a more
profound eavaluation of a system's generalization capability.

#### 1.3.2 The spectrum of generalization: robustness, flexibility and generality

> "... bien qu'elles fissent plusieurs choses aussi bien, ou peut-être mieux que nous, elles
> manqueraient infailliblement en quelques autres, par où on découvrirait qu'elles n'agiraient pas par
> connaissance, mais seulement par la disposition de leurs organes."
> 
> \- René Descartes, 1637

- Chollet takes generalization as the ability of a system to handle situations (or tasks) that
differ from previously encountered situations.

- To better understand what *previously encountered situations* means, we must distinguish between
two types of generalization.




---

## Reference

- [Chollet, F. (2019). On the measure of intelligence. arXiv preprint arXiv:1911.01547](https://arxiv.org/abs/1911.01547).