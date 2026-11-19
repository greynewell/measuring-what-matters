---
name: three-questions
description: Interrogate a metric with the three questions from the Measuring What Matters workshop (what does it hide, what behavior does it reward, what counter-balances it). Use when someone proposes, reviews, defends or wants to set a target on any engineering or productivity metric, or asks for metrics to track.
---

# The three questions

Three questions to ask of any metric before trusting it. They are this workshop's own practical tool, not an industry standard, so do not cite them as research.

1. **What does it hide?**
2. **What behavior does it reward?**
3. **What counter-balances it?**

## Before you start

Pin the metric down. A vague metric cannot be interrogated.

- **Definition:** what is counted or timed, and in what unit?
- **Boundaries:** for a time metric, where does the clock start and stop?
- **Level:** whose numbers are shown? Default to the team. Do not go below it.
- **Purpose:** what question is this metric meant to answer? If the person cannot say, stop and help them find the question first.

## Question 1: what does it hide?

Look for what the number cannot show.

- **Shape.** Is it an average of skewed data? Ask for the median and the p90. An average can stay flat while the typical case gets faster and the slow end gets slower.
- **Mix.** Does it lump unlike work together, such as one-line fixes with migrations?
- **Boundaries.** What happens before the clock starts or after it stops? Lead time that starts at the commit hides everything before the commit.
- **Size and quality.** A count says nothing about how big or how good each item was.
- **The people.** What would the team say about this that the number does not?

## Question 2: what behavior does it reward?

Name two behaviors, every time.

- **The intended one:** what you hope people do more of.
- **The lazy one:** the cheapest way to move the number without the improvement. Assume sensible people will find it. Gaming is rarely dishonest; it is people responding to what they are rewarded for.

If the metric will be a target, tied to a bonus, or shown per person, say plainly that the lazy behavior becomes much more likely.

## Question 3: what counter-balances it?

Find the tension metric: a second measure that gets worse when the first is hit the lazy way.

Ask: **if someone hit this number the lazy way, what would get worse?** Measure that.

Then check the pair:

- An improvement counts only when the first number moves and the second holds.
- Ask whether the tension metric can itself be gamed. If it easily can, pick another.
- Add one qualitative signal where no number will do, such as a pulse survey question.

## Output format

Answer in this shape, one block per metric, and keep each cell to a sentence.

| | |
| --- | --- |
| **Metric** | Name, definition, level |
| **It hides** | The one or two most important blind spots |
| **It rewards** | Intended behavior, and the lazy way |
| **Counter-balance** | The tension metric, and why it catches the lazy way |
| **Verdict** | Keep, keep with the pair, or drop, in a few words |

## Worked example

| | |
| --- | --- |
| **Metric** | Deployment frequency: production deployments per week, per team |
| **It hides** | How big each deployment is, and whether it worked |
| **It rewards** | Shipping small and often. Lazy way: splitting releases or shipping no-op changes to pad the count |
| **Counter-balance** | Change fail rate. Padding the count by shipping carelessly pushes it up |
| **Verdict** | Keep with the pair. Never set it as a target on its own |

Common pairs to start from:

| Primary metric | Tension metric |
| --- | --- |
| Deployment frequency | Change fail rate |
| Cycle time | Rework: reverts, hotfixes and follow-up fixes |
| Pull requests merged | Median pull request size, review depth |
| AI tool adoption | An outcome such as cycle time, paired with change fail rate |

## Do not

- Do not approve a metric that has no tension metric.
- Do not help set a target on a metric without naming the lazy way to hit it.
- Do not apply the questions to individuals' numbers. Recommend team level instead.
