---
name: space-framework
description: Check a set of developer productivity metrics for balance using the five SPACE dimensions (satisfaction and well-being, performance, activity, communication and collaboration, efficiency and flow). Use when someone asks whether they are measuring productivity in a balanced way, wants to design or audit a metric set or dashboard, mentions SPACE, or has a set made mostly of activity counts.
---

# The SPACE framework

SPACE is a framework of five dimensions for thinking about developer productivity, published in 2021 by Nicole Forsgren, Margaret-Anne Storey and colleagues in [The SPACE of Developer Productivity](https://queue.acm.org/detail.cfm?id=3454124).

**SPACE is a checklist, not a set of metrics.** It names what to cover and leaves the choice of measures to you. Do not present it as a list of things to track.

## The five dimensions

| | Dimension | Plain meaning | Example measures |
| --- | --- | --- | --- |
| **S** | Satisfaction and well-being | How fulfilled and healthy developers are | Satisfaction surveys, burnout, having the tools they need |
| **P** | Performance | Outcomes, as opposed to output | Quality, reliability, customer impact |
| **A** | Activity | Counts of things done | Commits, pull requests, reviews, deployments |
| **C** | Communication and collaboration | How well people work together | Review quality, findable documentation, onboarding time |
| **E** | Efficiency and flow | Progress without interruption or delay | Handoffs, interruptions, wait time |

## The paper's advice

- Cover **at least three** dimensions.
- Include **at least one perception measure**, such as a survey. Numbers from tools tell you what happened. People tell you why.
- Report at **team level**, with results anonymized.

## When SPACE is the right tool

Use it when the question is: **are we measuring productivity in a balanced way?**

For "is our delivery pipeline healthy?", use the `dora-metrics` skill. The two work together: DORA metrics can fill SPACE slots, mostly under Performance, Activity and Efficiency.

## What it does well

It forces balance. A dashboard made only of activity counts fails the SPACE test at a glance.

## What it misses

It offers example measures but no fixed set. You still have to choose, define and collect them, and each one still needs the `three-questions` skill run on it.

## How to audit a metric set

1. List every metric the person tracks or plans to track.
2. Place each one in a dimension. If a metric fits two, pick the one it mainly serves.
3. Mark each as **telemetry** (collected from tools) or **perception** (reported by people).
4. Check the three rules: three or more dimensions covered, at least one perception measure, team level.
5. Name the gaps, and suggest one measure for each empty dimension that matters to the person's question. Do not pad the set to fill all five.
6. For every metric kept, name its tension metric.

## Output format

| Metric | Dimension | Telemetry or perception | Level |
| --- | --- | --- | --- |
| ... | S, P, A, C or E | ... | Team |

Then three short lines:

- **Coverage:** which dimensions are covered and which are empty.
- **Rules:** pass or fail on three dimensions, one perception measure, team level.
- **Next step:** the one change that would most improve the balance.

## Common findings

- **All activity.** Commits, pull requests and lines of code only. Add a Performance outcome and a Satisfaction survey question.
- **No perception measure.** Add a short pulse survey: a handful of questions on a regular schedule.
- **Per-person numbers.** Move them to team level before doing anything else.
- **Telemetry and survey disagree.** Treat the disagreement as a finding. If cycle time looks fine and developers say reviews are slow, check the p90, then check what the metric's definition leaves out.

## A starter set that passes

The workshop's starter set is three metrics, a tension metric for each, and one qualitative signal. Run this audit on it before the pilot starts: the three metrics should not all sit in Activity, and the qualitative signal is the perception measure.
