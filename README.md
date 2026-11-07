# StudySkill

**English** | [简体中文](README.zh-CN.md)

### Let learning begin with a question of your own.

**Choose your direction · Learn through problems · Demonstrate understanding · Shape the next lesson**

What would learning look like if it began with your curiosity? If every attempt could change the next lesson? If the teacher had to reflect on their teaching, too?

StudySkill turns that idea into a repeatable approach to interactive teaching.

You choose what to explore. An AI tutor helps you plan a path. You try, explain, and revise as you work through concrete problems. Your questions, interests, and experience help determine what happens next.

> **You choose the direction. Practice reveals understanding. Your feedback changes the teaching.**

---

## Why StudySkill?

I want to challenge a familiar pattern in traditional education: students follow a predetermined sequence of content, with little say in which questions matter, how understanding is demonstrated, or how the teaching itself should change.

I want learners to be able to say:

“Why am I learning this?”

“I want to solve my own problem first.”

“I can already do this. Can we move on?”

“That explanation didn't help me understand. Let's try another way.”

And I want those words to actually change the course.

**The ambition is to give students a meaningful say in their goals, pace, and path—and make teaching respond to what they can do and how they experience learning.**

AI makes sustained, individual interaction easier to offer. Connecting choice, practice, feedback, and a lasting record gives that interaction a structure for deeper learning.

## Learn why a method exists

Behind many ideas lies a problem that people once struggled to solve.

A method helps, then meets a new limitation. New concepts, tools, and explanations emerge. Following those turning points helps us understand why a method appeared, why it works, and when to choose something else.

**StudySkill organizes teaching around the evolution of problems and methods. Concepts arrive with a reason to learn them.**

Learning about data storage, for example, might begin here:

```text
I want to save some records.
            ↓
A file is enough to get started.
            ↓
As records grow, finding and changing them gets awkward.
            ↓
I need better ways to organize and query the data.
            ↓
Now the records are related. How should I handle that?
```

This is a simplified teaching scenario. Real disciplines develop through branching ideas, parallel discoveries, and revisions; they rarely follow a single straight line.

There is no need to retrace every old path. Try an earlier method when it reveals an important problem. Summarize it when it offers useful context. Skip it when it adds little to the learner's goal. Judge its usefulness against the situation at hand.

## A course that changes with you

### 01 · Start with what you want to learn

Bring a subject, a question, a book, or something you want to make:

> I want to learn about databases, starting with why we need them.
>
> I want to understand how computers process language.
>
> I want to work through this mathematics book.
>
> I want to add a history feature to my app.

The tutor helps clarify your goal, identify necessary foundations, and agree on a manageable scope. Learning can serve curiosity, understanding, or a practical need. A software project or career outcome is never a required destination.

### 02 · See the path before taking the next step

Planning happens at two levels:

| Level | What you see in advance |
|---|---|
| Overall roadmap | Core questions, connections between learning rounds, milestones, rough effort, and completion criteria |
| Plan for each round | Why each section matters, what you will do, and how understanding will be assessed |

You review and approve the plans before teaching begins. Later rounds become more specific as you progress. A change of goal or a substantial change of route comes with an explanation and a decision for you to make.

### 03 · Let your attempts guide the explanation

A round might begin with a prediction, a design, or a small experiment. Your result reveals what needs explaining. The tutor introduces a concept, offers a hint or demonstration, and gives you room to try again.

When a foundation is missing, explain it clearly. When understanding is already demonstrated, move forward. Each task should produce something meaningful: a small working feature, a complete argument, a piece of writing, or a reasoned choice. Avoid drawn-out guessing games and endless edits to individual lines.

### 04 · Show what you understand

In programming, implement a feature. In mathematics, develop an argument and apply it to a variation. In writing, produce a text and explain your revisions.

Assessment asks:

- Can you complete the task?
- Can you explain the important choices?
- Can you adapt your method when the conditions change?

Independent work, prompted work, following a demonstration, and work done by the AI are recorded separately. Skip what you have already demonstrated. Address the specific gaps that remain.

### 05 · Evaluate the teaching, too

Reflection includes your experience as well as the tutor's observations.

What finally made sense? What remains unclear? Was the pace too fast, or were the tasks too fragmented? What felt repetitive? What made you want to explore further?

That feedback should produce concrete changes:

| Your feedback | How the next round can change |
|---|---|
| “The tasks are too fragmented. I can't see what we're building.” | Show the complete goal first, then combine small edits into a useful feature. |
| “The example works, but I can't explain why.” | Add explanation, prediction, and a variation that exposes the gap in understanding. |
| “I want to understand the principles before making a full project.” | Agree on a revised route built around reasoning, small experiments, and discussion. |
| “I already know this.” | Check the available evidence and skip repeated practice. |

**The next plan must explain what you said and what changed because of it.**

### 06 · Keep the process, then pick up where you left off

Meaningful learning steps are recorded: the problem, your attempt, the tutor's help, the observed result, the basis for assessment, and the changes prompted by feedback.

When you return, the record identifies where you stopped and what remains unfinished. Looking back, you can trace how your understanding developed—and whether the teaching followed through on its promises.

## What an exchange could look like

This example illustrates the intended interaction. It is not evidence of learning outcomes.

> **Student:** I want to learn about databases by adding history to my small app.
>
> **Tutor:** Let's clarify what you want to save and how you'll retrieve it, then agree on a roadmap. This round will produce a working way to save and read history. You'll see the tasks and assessment criteria before we start.
>
> **Student:** I saved the records, but searching by a condition is awkward.
>
> **Tutor:** That's the next problem to investigate. Let's look at how you're searching now, then consider how to organize the data and express the query.
>
> **Student:** We keep changing one line at a time. I've lost sight of the whole thing.
>
> **Tutor:** Let's show the complete flow and group the related changes into one useful feature. I'll record that feedback in the reflection and carry it into the next plan.

## Get started

This repository provides a teaching skill for an AI assistant that can read skill files. It defines the teaching workflow and recordkeeping conventions; it does not currently include a standalone teaching app.

1. Use this repository as a separate learning workspace.
2. Have your assistant load the [StudySkill instructions](.agents/skills/studyskill/SKILL.md). Environments with compatible Agent Skills discovery can find `.agents/skills/studyskill/`.
3. Tell the assistant what you want to learn. Where explicit skill invocation is supported, start with:

```text
$studyskill

I want to learn ________.
My current background is ________, and I hope to be able to ________.
Help me clarify my goal, then propose an overall roadmap
and a plan for the first learning round.
```

You do not need a fully formed goal. Start with what makes you curious. Once learning begins, records are saved under `learning/` in the workspace, separately for each topic.

## Inside the repository

| File | Purpose |
|---|---|
| [SKILL.md](.agents/skills/studyskill/SKILL.md) | Entry point and core teaching workflow |
| [planning-and-teaching.md](.agents/skills/studyskill/references/planning-and-teaching.md) | Planning at both levels, selecting problems and methods, and guiding interaction |
| [reflection.md](.agents/skills/studyskill/references/reflection.md) | Student experience, tutor reflection, and changes to future teaching |
| [records.md](.agents/skills/studyskill/references/records.md) | Progress, events, evidence, and resuming learning |
| [AGENTS.md](AGENTS.md) | Workspace instructions and boundaries |

The teaching specifications are currently written in Chinese. This README provides an English introduction to the project.

StudySkill is maintained independently, with its own course records. It is separate from the original ai-job-search `/upskill` workflow and its existing learning history.

## An approach to keep testing in practice

The current version defines teaching, assessment, reflection, and recordkeeping rules. The experience still depends on the assistant executing them, the quality of the materials, and the participation of both learner and tutor. These specifications do not establish independently validated learning outcomes.

Real learning experiences can help improve the approach. Which question made something click? Which interaction became frustrating? Which piece of feedback failed to change the teaching?

Those experiences give StudySkill reasons to revise its own methods.

---

**Start with the question you truly want to understand.**
