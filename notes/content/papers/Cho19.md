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

The main goal of the AI field since its inception has been to create systems with human-like 
intelligence. However, Chollet argues that this goal is unachievable given that there isn't a clear 
definition of intelligence, nor a standard way to measure it.

In this context, he proposes a **formal definition of intelligence**, and a set of guidelines for
**how a general AI benchmark should look**. To illustrate this, he introduces the [**Abstraction and 
Reasoning Corpus (ARC)**](https://github.com/fchollet/ARC-AGI), as a tool for evaluating
artificial *fluid* intelligence.

---

## 1 Context and History

### 1.1 Need for an actionable definition and measure of intelligence

We have been able to engineer systems that excel at specific tasks, but they still have limitations:
they struggle to work from little data and to adapt themselves to novel situations for which they
were not trained.

The root of the problem behind this is the **lack of a clear definition of intelligence**, despite the
the 70 years of AI history. With no clear definition, there is no concrete goal to pursue. Even worse,
**there is no established standard way to measure it**.

Then, it becomes obvious that we need two things:
- A clear definition, actionable, explanatory and **measurable** definition of intelligence.
- A standard and reliable way to measure it.

Chollet points out that the AI community has often neglected efforts to establish formal definitions
and evaluation methods, which he sees as a mistake. That is why, he focuses on identifying
the implicit assumptions on which the field has been working, and attempts to correct them.

### 1.2 Defining intelligence: two divergent visions

We start then analyzing the field's current state. *Legg and Hutter (2007)* summarized 70 definitions
of intelligence into:
"*Intelligence measures an agent's ability to achieve goals in a wide range of environments*".

This definition lets us extract two key components:
- *to achieve goals*: task-specific skill
- *in a wide range of environments*: capability of generalization and adaptation

Implicit in the second one, is the fact that an agent must be capable of learning how to handle new
tasks (*skill acquisition*) for it to truly be general.

The two components of that definition map themselves to the main views of the human's mind
nature: one sees the mind as a static assembly of special-purpose mechanisms developed
through evolution and set to only learn what it was programmed to, and the other sees
the mind is a blank slate (Tabula Rasa) capable of turning experience into knowledge and skills.

We must then analyze these perspectives before we can formulate our own definition.

![perspectives](/images/perspectives.png#small "Two perspectives")

#### 1.2.1 Intelligence as a *collection of task-specific skills*

Originated in Darwin (1859), this view considers the mind as a collection of special-purpose
adaptations developed by humans to solve specific problems faced during evolution.

To the AI community, this view served as a basis for developing their definition of intelligence.
They considered intelligence as a set of static, program-like routines, relying on logical operators
for problem-solving, and a database-like memory for knowledge storage.

It then became popular in the field to believe that the "problem of intelligence" would be solved
if we could better encode human skills into formal rules and knowledge into databases. This resulted
in evaluation protocols based on performance in specific tasks.

As pointed out by *Hernández-Orallo (2017)*, this view resulted in a paradox: "*The AI field
became successful in developing artificial systems that could perform very well on specific tasks
without featuring intelligence at all*". This trend persists today.

#### 1.2.2 Intelligence as a *general learning ability*

The alternative view is based on the idea that intelligence lies in the ability to acquire new
skills through learning. Such and ability could then apply to a wide range of unseen—or even any—
problems.

This perspective aligns with the cognitive science view of the mind as a blank slate:
a flexible, adaptable, highly general process that transforms experience into behavior, knowledge and
skills.

Although this idea of generality through learning was at the core of AI at the birth of the field,
it wasn't until the 1980s, with the revolution in deep learning, that it gained serious attention.
It was during this peak that many researchers began to conceptualize the mind as a "*randomly
initialized neural network*" that starts blank and derives skills from training data. As Chollet 
states, we see the world through the lens of the tools we are most familiar with.

Today, it has become obvious that both perspectives—whether a collection of special-purpose
programs or a general-purpose Tabula Rasa—are incorrect.

### 1.3 AI evaluation: from measuring skills to measuring broad abilities

It’s not only the lack of a clear definition that is concerning, but also the methods of evaluation.
Neither of the two perspectives discussed so far has established a formal approach for comprehensive
evaluation.

#### 1.3.1 Skill-based, narrow AI evaluation

Historically, system evaluation has included:
- *Human review*: Human judges observe input-output pairs and score them. However, this method
is expensive, impossible to automate or scale, and subjective.
- *White-box analysis*: Systems are analyzed internally. This approach is useful for verifying if
they operate as intended.
- *Peer confrontation*: Systems compete against each other to find the best one.
- *Benchmarking*: Systems produce outputs for which *test sets* have been defined,
and desired outputs are known.

In particular, **benchmarks** are considered the best tools for evaluation because they are 
reproducible, fair, scalable, relatively easy to set up, and flexible enough to be applicable to
a wide range of tasks.

However, benchmarks carry a hidden pitfall: they might encourage systems to overly optimize for a
specific metric or task, limiting generalization to other tasks—thus not aligning with human-like 
intelligence.

For *humans*, excelling at a specific task is considered proof of intelligence because
it demonstrates the implicit general ability we must have had in the first place to learn that task.
Furthermore, it suggests we could extend this ability to other tasks or domains.

For *machines* this is not the case. Machines excelling at specific tasks does not prove they
are intelligent. And this leads back to the earlier paradox: "Artificial systems can solve
complex problems without being intelligent at all".

This confusion arises because, in humans, the intelligence process (the ability to learn many
skills) and the artifact produced by this process (good results on particular tasks) 
are intertwined. In other words, for humans being good at one task is enough proof of intelligence,
while for machines it is just that: being good at one task.

![just-that](/images/just-that.png#small "Just that")

The problem then with the AI field has not been that AI systems have been measured by their
performance on specific tasks. Rather, the issue has been interpreting these results as proof of
of success towards developing systems capable of autonomy and dynamic adaptability like humans.

We must therefore correct how success is measured, focusing specifically on aspects that
current problems in the field exhibit: the need of *flexibility* and *robustness*.
Moreover, it has become clear that we need to move beyond skill-based evaluation, to a more
profound assessment of systems' generalization capabilities.

#### 1.3.2 The spectrum of generalization: robustness, flexibility and generality

> "... bien qu'elles fissent plusieurs choses aussi bien, ou peut-être mieux que nous, elles
> manqueraient infailliblement en quelques autres, par où on découvrirait qu'elles n'agiraient pas par
> connaissance, mais seulement par la disposition de leurs organes."
> 
> \- René Descartes, 1637

Chollet *informally* defines generalization as the ability of an AI system to handle situations or
tasks that differ from previously encountered ones. To understand what *previously encountered 
situations* means, we must distinguish between two types of generalization:
- *System-centric generalization*: Ability of a learning system to handle situations it has
never seen before. If an engineer develops a machine learning algorithm and fits it on
a training set of N samples, its generalization capability would refer to the classification
error over images not included in the training set.
- *Developer-aware generalization*: Ability of a system—either learning or static—to handle
situations neither the system nor its developer has seen before. Continuing the previous example,
this would mean evaluating algorithm performance on data completely outside its training and 
development contexts.

Furthermore, degrees of generalization can be qualitatively defined as:
- *Absence of generalization*: Generalization requires uncertainty—information unknown to the system
or developer. Deterministic systems (e.g., chess engines, array sorters) involve no uncertainty,
thus no generalization.
- *Local generalization* or **robustness**: Ability of a system to handle new data points from a
known distribution for a single task or set of tasks, given a sufficiently dense sampling
of examples. Simplified: *adaptation to **known unknowns within a single task** or well-scoped
set of tasks*. This form of generalization has dominated the field since the 50s.
- *Broad generalization* or **flexibility**: Ability of a system to handle a broad range of tasks
and environments without further human intervention (developer-aware generalization). Simplified:
*adaptation to **unknown unknowns across diverse related tasks***. Even the most advanced AI
systems today do not belong to this category.
- *Extreme generalization* or **generality**: Ability of open-ended systems to handle entirely new
    tasks that only share abstract commonalities with previously encountered situations, applicable
    to any task and domain within a wide scope. Simplified: *adaptation to **unknown unknowns across
    an unknown range of tasks** and domains*.
        
Chollet refers, in particular, to "*human-centric extreme generalization*" as *generality*, because
**humans are the only known systems** that can **display both system-centric** (quick adaptability to 
novel situations from little experience) **and developer-aware generalization** (ability of
contemporary humans to handle situations that previous ones in history have never encountered).

One additional category could be noted: *universal generalization* or **universality**, which extends
the notion of *generality* beyond the scope of humans. However, this lies outside the goals of the AI
field, and Chollet considers it irrelevant. 


---

## Reference

- [Chollet, F. (2019). On the measure of intelligence. arXiv preprint arXiv:1911.01547](https://arxiv.org/abs/1911.01547).