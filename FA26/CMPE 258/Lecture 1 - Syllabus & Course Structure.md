---

title: "Lecture 1 - Introduction to Deep Learning" course: CMPE 258-02 Deep Learning instructor: Dr. Kaikai Liu institution: San Jose State University term: Fall 2026 date: 2026-08-20 tags:

- cmpe258
- deep-learning
- lecture-notes
- syllabus source: "CMPE258 Lecture1 Introduction 0820.pdf"

---

# Lecture 1 — Introduction to Deep Learning

> [!info] Course info **CMPE 258-02, Deep Learning** — Dr. Kaikai Liu, Associate Professor, Dept. of Computer Engineering, SJSU 📧 kaikai.liu@sjsu.edu · 🏫 ENG257, SJSU · Fall 2026

## TL;DR

- Deep learning (DL) is a subfield of [[Machine Learning]] using neural networks loosely inspired by the brain; it automates [[feature extraction]] that classical ML does by hand.
- The AI stack nests: **AI ⊃ ML ⊃ DL ⊃ LLM**, with large LLMs often also counted as **GenAI**.
- ML flips the traditional programming model: instead of `program + data → output`, ML does `data + output → program`.
- Modern DL systems display **[[emergence]]** and follow **[[scaling laws]]** — capability jumps unpredictably as models scale, even though loss decreases smoothly.
- The core goal of ML/DL is **[[generalization]]**: performing well on new, unseen data, not just memorizing the training set.
- Course grading: 5% quizzes, 15% homework, 20% midterm, 30% final, 30% team project (1–3 people).

---

## 1. What is Deep Learning?

> [!quote] Definition Deep Learning is a part of machine learning that deals with algorithms inspired by the structure and function of the human brain. It uses artificial neural networks to build intelligent models and solve complex problems.

- Sits inside the broader **[[Machine Learning]]** field.
- Uses **artificial neural networks** as the core modeling tool.

## 2. The AI / DL / GenAI / LLM Taxonomy

Nested subsets, from broadest to narrowest:

```
AI
└── Machine Learning
    └── Deep Learning
        └── LLMs (Large Language Models)
```

- **LLMs** are a subset of DL models, which are a subset of ML models, which are a subset of AI.
- Depending on size/capability, LLMs can also be considered **Generative AI (GenAI)** models.

> [!note] Old vs. new answer to "What is AI?"
> 
> - **Old answer**: classic symbolic/search-based AI, e.g. _Artificial Intelligence: A Modern Approach_ (Russell & Norvig) — see [aima.cs.berkeley.edu](http://aima.cs.berkeley.edu/2nd-ed/books.html). Peter Norvig — Director of Research at Google.
> - **New answer**: today's answer is framed around the recent, rapid advancements in AI (i.e., DL/LLMs) rather than symbolic reasoning alone.

## 3. Traditional Programming vs. Machine Learning

_(Slide credit: Pedro Domingos)_

||Traditional Programming|Machine Learning|
|---|---|---|
|Inputs|Program + Data|Data + Output|
|Output|Output|**Program** (the learned model)|

- ML gives computers the ability to learn **without explicit programming**.
- Instead of a human writing rules, the system infers the "program" (model) from data + desired outputs.

## 4. Motivating Example: Autonomous Driving

- Tesla's **Autopilot/FSD** framing: end-to-end AI from _images in_ → _steering, brakes, acceleration out_, dropping **300k+ lines of C++ control code** in favor of a learned, data-driven system.
- ML helps solve **corner cases** (rare, dangerous, unexpected driving scenarios) by:
    - Learning from massive datasets
    - Generalizing beyond explicit programming
    - Adapting to new, unseen situations
- Modern LLMs show strong generalization in translation, coding, text generation.
- **[[Imitation Learning]] (IL)**: an agent learns a skill by observing/mimicking an expert's demonstrations — learns a state→action mapping _without_ a hand-defined reward function. Useful for teaching complex tasks (e.g., driving).

## 5. Key Essence of Machine Learning

For ML to apply, four conditions should hold:

1. There exists some **underlying pattern** to be learned.
2. A **performance measure** can be improved by learning it.
3. There is **no easy/programmable definition** of that pattern.
4. There is **data** about the pattern to learn from (i.e., "inputs").

> [!important] Generalization Generalization — applying learned patterns to new, unseen, real-world data (not just memorizing training data) — is the **single most important property** of an ML system. **Poor generalization → overfitting.**

### Learning = Generalization (H. Simon, 1983)

> "Learning denotes changes in the system that are adaptive in the sense that they enable the system to do the task or tasks drawn from the same population more efficiently and more effectively the next time."

- Practically: the ability to perform a task in a situation **never encountered before**.

## 6. The Machine Learning Lifecycle

Two parallel loops:

**Offline (model development)** `Data Collection → Cleaning & Visualization → Feature Eng. & Model Design → Training & Validation → Trained Model`

- Roles: Data Scientist, Data Engineer

**Online (serving)** `Live Data → Prediction Service (Inference) → End User Application → Query/Prediction → Feedback Logic → back into training data`

> [!tip] Takeaway ML is not just training a model once — it's a **pipeline** connecting offline training data/pipelines to a live, feedback-driven prediction service.

## 7. Deep Learning vs. (Shallow) Machine Learning

- DL is a **sub-class of ML** algorithms distinguished by higher architectural complexity — not a separate/opposing concept.
- "**Shallow learning**" = ML techniques that are _not_ deep.
- Why does added complexity help?
    - Like human learning, information is absorbed **step by step**: early layers learn specific/local concepts, deeper layers build **abstract concepts** from earlier representations.
    - This automatic construction of representations from raw data is **[[feature extraction]]**.
    - DL architectures can perform feature extraction **automatically**.
- **Shallow/classical ML**: feature engineering is done _outside_ the algorithm, by human data scientists analyzing raw data.
- **Deep learning is often described as a "black box."**

> [!note] More data → better performance A recurring theme: DL models tend to keep improving as more data (and compute/parameters) are available — this connects directly to [[scaling laws]] below.

## 8. Emergence in Deep Learning

- In most of computer science, **emergence** is associated with bugs/unintended behavior — systems are built to be **modular**, decomposed into parts solved individually and recombined.
- In **deep learning (including LLMs), emergence is necessary, not accidental**:
    - Only the **network structure** and **training algorithm** are explicitly designed.
    - Every ability / internal property the network ends up with is **emergent** from training, not hand-coded.

### Scaling Laws

- A research area studying how well language models of different scales predict the next token/word.
- As LLMs train with more **compute, data, and parameters**, they generally get better at predicting held-out/training text (loss decreases smoothly/predictably).

### Emergent Abilities of LLMs

- **Perplexity/test loss** changes **smoothly** as models scale.
- Performance on **individual tasks** is often **choppy/discontinuous**:
    - Example: 3-digit addition — poor performance until a scale threshold, then a **sudden jump**.
- So: smooth scaling-law improvement in aggregate loss can coexist with **sudden, unpredictable emergent jumps** in specific task capabilities.

> [!question] Discussion prompt Is an "emergent ability" a real discontinuity in capability, or partly an artifact of using a discontinuous evaluation metric (e.g., exact-match accuracy)? Worth revisiting once we cover evaluation methodology.

## 9. Why Learn Deep Learning?

- **Unprecedented performance** across vision, speech, NLP tasks; handles complex patterns + large datasets well.
- **Data abundance**: thrives in the big-data era.
- **Automation & efficiency**: automates traditionally manual tasks (healthcare, manufacturing, finance).
- **Innovation**: underlies self-driving cars, personalized medicine, recommendation systems.

## 10. Course Learning Objectives

By the end of the course, students should be able to:

- Demonstrate comprehensive understanding of deep neural network architecture & principles.
- Apply DL algorithms/models across different problem domains.
- Analyze/evaluate DL model performance with appropriate metrics/techniques.
- Implement, train, and fine-tune deep neural networks with popular DL frameworks.
- Collaborate effectively (individually and in groups) on real-world DL challenges.
- Demonstrate **ethical awareness** of bias/considerations in DL applications.

---

## 11. Grading Breakdown

|Component|Weight|
|---|---|
|Quiz (in-class mini-quiz)|5%|
|Homework & Assignments|15%|
|Midterm Exam|20%|
|Final Exam|30%|
|**Team Project** (1–3 people)|30%|

_(Midterm + Final = 50% combined)_

### Homework Grading — EMRN Rubric

- Four-level specification grading: **E**xcellent / **M**eets expectations / **R**evision needed / **N**ot assessable.
- E and M → full marks; R and N → lower marks per assignment spec.
- One revision period per assignment.
- Getting an "E" doesn't change overall grade **but** students targeting **A/A+** must earn **at least one "E"** on a homework.
- Students who earn "E" may be asked to **present their solution** in class.
- Suspiciously similar solutions/code without proper citation/justification → **score of 0**.

### Other Grading Policies

- Final grades computed from weighted totals across exams/HW/projects; letter grade cutoffs (A–E) are set to satisfy distribution/policy requirements — raw point anxiety ≠ predictive of final letter grade.
- **No extra credit.**
- Re-evaluation requests only if the **evaluation itself was wrong**.
- **Peer ratings/comments** factor into project scores.
- Late Canvas submissions after the assignment closes → **zero**.
- Turnitin-enabled assignments must be submitted as **Word or PDF**, else treated as late.

## 12. Class Policies

- Students are responsible for lecture content, book sections, project presentations, and any in-class instructions.
- **No web browsing** during class; computers only for course-related activity (notes, following slides, instructor-directed sites).
- Repeated disruption → referral to Judicial Affairs Officer.
- Excused absences: notify instructor **before** the scheduled quiz/exam with documentation to reschedule. No makeup otherwise.
- **All exams are closed book, closed notes.** Sharing exam Q/A is prohibited.
- Re-evaluation requests go through the Instructor's Student Assistant (ISA); attempting to pressure/coerce the ISA or instructor → score of 0.
- **Team projects (1–3 students)**: instructor does not help find teammates. Non-contributing teammates must be warned in writing (CC instructor); can be removed from the team with instructor notice **≥1 month before** the project deadline.

## 13. Generative AI Use Policy (Projects & Assignments)

- GenAI tools are **allowed and encouraged** for brainstorming, coding assistance, debugging, documentation.
- **Producing code is not the goal — evaluation is.** Submissions must show evidence the system works, and _how well_.
- Every major function must be evaluated via **at least one** of:
    - A working functional demo (screenshots / video / logs / results), and/or
    - Quantitative evaluation with appropriate metrics (with setup explained).
- **Academic integrity is mandatory**: submitting non-working code while fabricating/falsifying results (including presenting generated outputs as real experiments) → **score of 0**, may be referred under the course integrity policy.

> [!warning] Key implication for the team project Whatever project we pick (see [[CMPE 258 Project Ideas]]), we must design in a **real evaluation plan** (metrics and/or demo) from day one — this is graded, not optional polish.

---

## My Questions / Follow-ups

- [ ] How exactly will "meaningful contribution" be judged for the team project — novelty vs. solid execution/evaluation?
- [ ] Which DL framework(s) will the course standardize on (PyTorch presumably — confirm)?
- [ ] Clarify what counts as an acceptable "excused absence" and documentation.

## Related

- [[CMPE 258 Project Ideas]]
- [[Machine Learning]]
- [[Scaling Laws]]
- [[Emergence]]
- [[Generalization]]
- [[Imitation Learning]]