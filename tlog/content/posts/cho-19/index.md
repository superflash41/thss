+++
title = "Cho19 - on the measure of intelligence"
date = "2025-01-30"
math = true
hideBackToTop = true
draft = false

[cover]
image = "cover.jpeg"
alt = "intro"
relative = true
hidden = false
+++

## overview

the main goal of the AI field since inception has been to create systems with human-like intelligence.  Chollet argues this goal is unachievable because there hasn't been a clear definition of intelligence, nor a standard way to measure it.

in this paper, he proposes a **formal definition of intelligence**, and a set of guidelines for how a **general AI benchmark** should look like. he introduces the *[Abstraction and Reasoning Corpus](https://github.com/fchollet/ARC-AGI)*.

---

## 1 context and history

### 1.1 need for an actionable definition and measure of intelligence

we have AI systems that excel at specific tasks, but they still have **limitations** when working with little data and when trying to adapt to novel situations for which they were not trained.

the root of the problem is the **lack of a clear definition of intelligence**, despite the 70 years of AI history. with no clear definition, there is no concrete goal to pursue.

then, it becomes obvious that we need two things:
- a clear, actionable, explanatory and **measurable** definition of intelligence.
- a **standard** and reliable way to measure it.

Chollet points out that the AI community has often neglected efforts to establish (the very much needed) formal definitions and evaluation methods. so, he focuses on identifying the **wrong assumptions** on which the field has been working, and attempts to correct them.

### 1.2 defining intelligence: two divergent visions

he starts analyzing the field's current state. *Legg and Hutter (2007)* summarized 70 definitions of intelligence into:

> "intelligence measures an agent's ability to achieve goals in a wide range of environments".

this definition lets him extract two key components:
- *to achieve goals*: **task-specific skill**
- *in a wide range of environments*: capability of **generalization** and adaptation

implicit in the second one, is the fact that an agent must be capable of **learning how to handle new tasks** (*skill acquisition*) for it to truly be general.

the two components map to the main views of the human mind's nature:
- one sees the mind as a **static assembly** of special-purpose mechanisms developed through evolution to handle **specific tasks** crucial for survival.
- the other one sees the mind is a **flexible** blank slate (*Tabula Rasa*) capable of turning experience into knowledge and skills.

![perspectives](/perspectives.png#small "Two perspectives")

he analyzes these perspectives before formulating his own definition.

#### 1.2.1 intelligence as a *collection of task-specific skills*

originated in [Darwin](https://en.wikipedia.org/wiki/Darwinism) (1859), this view considers the mind as a collection of special-purpose adaptations developed by humans to **solve specific problems** faced during evolution.

to the AI community, this view served as a basis for their definition of intelligence. they considered it a set of **static**, program-like routines, relying on **logical operators** for problem-solving, and a **database-like memory** for knowledge storage.

it then became popular to believe that the *problem of intelligence* would be solved if we could better encode human skills into formal rules and knowledge into databases. this resulted in **evaluation protocols based on performance at specific tasks**.

![evolution](/evolution.jpg "The evolutionary perspective")

as pointed out by *Hernández-Orallo (2017)*, this view resulted in a paradox:

> "the AI field became successful in developing artificial systems that could perform very well on specific tasks **without featuring intelligence at all**".

this trend persists today.

#### 1.2.2 intelligence as a *general learning ability*

the alternative view states that intelligence lies in the ability to **acquire new skills through learning**. such an ability could then apply to a wide range of unseen (or even any) problems.

this perspective aligns with the cognitive science view of the mind as a blank slate: a **flexible**, **adaptable**, **highly general** process that transforms experience into knowledge and skills.

although **this idea of generality through learning was at the core of AI** at first, it wasn't until the 1980s (with the revolution in deep learning) that it gained serious attention. During this peak many researchers began to conceptualize the mind as a *randomly initialized neural network* that starts blank and derives skills from training data.

we see the world through the lens of the tools we are most familiar with.

![blank slate](/tabula-rasa.jpg "The skill acquisition perspective")

today, it has become obvious that **both perspectives**, whether a collection of special-purpose programs or a general-purpose Tabula Rasa, **are incorrect**.

### 1.3 AI evaluation: from measuring skills to measuring broad abilities

to Chollet it is not only concerning the lack of a clear definition, but also the lack of evaluation methods. **none** of the two perspectives has a **formal** approach for **comprehensive evaluation**.

#### 1.3.1 skill-based, narrow AI evaluation

historically, system evaluation has included:
- *human review*: human judges **observe input-output** pairs and **score them**. this method is **expensive**, impossible to automate or scale, and **subjective**.
- *white-box analysis*: systems are **analyzed internally** to check if they operate as intended.
- *peer confrontation*: systems **compete against each other** to find the best one.
- *benchmarking*: systems produce **outputs for which *test sets* have been defined**, and desired outputs are known.

**benchmarks** are considered the best tools for evaluation because they are **reproducible**, **fair**, **scalable**, relatively easy to set up, and **flexible** enough to be applicable to a wide range of tasks.

however, they carry a **hidden pitfall**: they may encourage systems to overly optimize for a specific metric or task, **limiting generalization** to others. in AI, the focus on achieving task-specific performance while placing no conditions on *how the system achieves it* has led to the development of systems that **lack the sort of human-like intelligence** that the field aspires to.

this was interpreted by McCorduck as an *AI effect*, and noted by Reed as:

> "when we know how a machine does something 'intelligent', it ceases to be regarded as intelligent. if I beat the world's chess champion, I'd be regarded as highly bright."

this (wrong) interpretation arises from overly anthropocentric assumptions about intelligence. 

for *humans*, excelling at one specific task is considered proof of intelligence because it demonstrates the **implicit general ability one must have had in the first place to learn that task**. furthermore, it suggests this ability could be extended to other tasks or domains.

for *machines* **this is not the case**. so the problem comes from confusing the **intelligence process** (the ability to learn many skills) and the **artifact produced** by this process (good results on particular tasks using those skills), given that in humans they are **intertwined**. for machines being good at one task is just that: being good at one task.

![just-that](/just-that.png#small "Just that")

the **problem** then has not been measuring AI systems by their performance on specific tasks. Rather, the issue has been **interpreting these results as proof of success** towards developing adaptable and autonomous human-like systems.

Chollet decides to **correct *how* this success is measured**, focusing on aspects the current field problems exhibit: the need of *flexibility* and *robustness*. moreover, it becomes clear to him that we need to **move beyond skill-based evaluation**, to a more profound assessment of systems' generalization capabilities.

#### 1.3.2 the spectrum of generalization: robustness, flexibility and generality

> "... bien qu'elles fissent plusieurs choses aussi bien, ou peut-être mieux que nous, elles manqueraient infailliblement en quelques autres, par où on découvrirait qu'elles n'agiraient pas par connaissance, mais seulement par la disposition de leurs organes."
> 
> \- René Descartes, 1637

Chollet *informally* defines **generalization** as the **ability of an AI system to handle situations or tasks that differ from previously encountered ones**. these *previously encountered situations* relate themselves with two types of generalization:
- *system-centric generalization*: ability of a learning system to handle situations **it** has never seen before. if an engineer fits a machine learning algorithm on a training set of $N$ samples, its generalization capability would refer to the classification error over images not included in the training set, but that are similar to those in it.
- *developer-aware generalization*: ability of a (learning or static) system to handle situations **neither the system nor its developer** has seen before. on the previous example, this would mean evaluating the algorithm on data completely outside its training and development sets.

additionally, he defines degrees of generalization:
- *absence of generalization*: Generalization requires uncertainty—information unknown to the system or developer. Deterministic systems (e.g., compilers, array sorters, deterministic mathematical functions) involve **no uncertainty**, thus **no generalization**.
- *local generalization* or **robustness**: Ability of a system to handle new data points from **a known distribution** for a single task or well-scoped set of tasks, given a sufficiently dense sampling of examples. Simplified: *adaptation to **known unknowns within a single task** or well-scoped set of tasks*. this form of generalization has dominated the field since the 50s.
- *broad generalization* or **flexibility**: Ability of a system to handle a broad range of tasks and environments **without further human intervention** (developer-aware generalization). Simplified: *adaptation to **unknown unknowns across diverse related tasks***. Even the most advanced AI systems from today do not belong to this category.
- *extreme generalization* or **generality**: Ability of open-ended systems to handle entirely new **tasks that only share abstract commonalities** with previously encountered situations, applicable to any task and domain within a wide scope. simplified: *adaptation to **unknown unknowns across an unknown range of tasks** and domains*.

![generalization](/generalization.jpg "The spectrum of generalization")
        
Chollet refers, in particular, to "*human-centric extreme generalization*" as *generality*, because **humans are the only known systems** that can **display both system-centric** (quick adaptability to  novel situations from little experience) **and developer-aware generalization** (ability of contemporary humans to handle situations that previous ones in history have never encountered).

one additional category could be noted: *universal generalization* or **universality**, which extends the notion of *generality* beyond the scope of humans. however, this lies outside the goals of the AI field, and Chollet considers it irrelevant. 


---

## reference

- [Chollet, F. (2019). On the measure of intelligence. arXiv preprint arXiv:1911.01547](https://arxiv.org/abs/1911.01547).