---
name: dora-metrics
description: Explain, compute and critique the five DORA software delivery metrics (change lead time, deployment frequency, failed deployment recovery time, change fail rate, deployment rework rate). Use when the question is about delivery speed or stability, when someone mentions DORA, the four keys, lead time, MTTR or change failure rate, or wants to know whether their delivery pipeline is healthy.
---

# DORA metrics

DORA (DevOps Research and Assessment) is a long-running research program, now part of Google Cloud. It is best known for a small set of software delivery metrics. Many people still call them the "four keys". The current guide lists five, in two groups.

Source: [DORA's software delivery performance metrics](https://dora.dev/guides/dora-metrics/). Check it before quoting a definition word for word; the set has changed over the years.

## The five metrics

| Group | Metric | Plain meaning | What you need to compute it |
| --- | --- | --- | --- |
| Throughput | Change lead time | Time from committed code to running in production | Commit timestamps and deployment timestamps |
| Throughput | Deployment frequency | How often you deploy to production | A log of production deployments |
| Throughput | Failed deployment recovery time | How long it takes to recover when a deployment fails | When each failed deployment started and when service recovered |
| Instability | Change fail rate | Share of deployments that need immediate intervention | Deployments, each marked as needing a rollback or hotfix or not |
| Instability | Deployment rework rate | Share of deployments that are unplanned fixes for a production incident | Deployments, each marked planned or unplanned |

Older material calls recovery time "MTTR" or "time to restore service".

## When DORA is the right tool

Use it when the question is: **is our delivery healthy, and is it improving?**

It is not the right tool for "are our developers productive?" or "is the team happy?". For a balanced view, use the `space-framework` skill and let DORA metrics fill some of its slots.

## What it does well

- It reports speed and stability side by side, so going faster by breaking more shows up. Throughput and instability are a built-in tension pair.
- It works best for tracking one service or one team against its own past.

## What it misses

- **Its clock starts at the commit.** Planning, waiting and design time before the first commit are invisible.
- **It says nothing about how the work feels.** DORA's wider research does study culture and well-being, so this limit belongs to the five metrics, not to the program.
- It describes the delivery pipeline, not whether the right thing was built.

## How to read the numbers

- For the time metrics, report the **median and the p90**, not only the mean. Time data is skewed: most changes are quick and a few are very slow.
- Compare a team with its own history. Look at the trend over months, not a single week.
- Read throughput and instability together. Throughput rising while instability rises is not an improvement.

## Warnings to repeat when relevant

These follow DORA's own guidance.

- **Do not turn the metrics into goals.** "Double deployment frequency" as an objective invites split releases and no-op deployments.
- **Do not rely on one metric alone.**
- **Do not use them to rank teams** or to compare unlike applications.
- **Do not report them per person.**

## AI tools and DORA

DORA's 2025 report, [State of AI-assisted Software Development](https://services.google.com/fh/files/misc/2025_state_of_ai_assisted_software_development.pdf), surveyed nearly 5,000 technology professionals and found 90% using AI at work. Higher AI adoption went with higher delivery throughput and also higher instability. The report describes AI as an amplifier of what is already there.

So when someone measures an AI tool with a throughput metric, always put an instability metric beside it.

## With this repository's dataset

`pull_requests.csv` is pull request data, not deployment data. Be exact about what it can stand in for.

| DORA metric | In this dataset |
| --- | --- |
| Change lead time | Not available. `cycle_time_hours` runs from pull request opened to merged, which is a different clock |
| Deployment frequency | Not available. Pull requests merged per month is a related count, not the same thing |
| Failed deployment recovery time | Not available |
| Change fail rate | Approximated by the mean of `change_failed`, per change and not per deployment |
| Deployment rework rate | Not available |

Say "approximately" when you use the approximation, and remember the data is invented.

## Output format

When asked to assess delivery with DORA, give:

1. The five metrics, each with its value or "not available from this data".
2. Median and p90 for each time metric.
3. One sentence on throughput and instability read together.
4. What DORA cannot see here, and what to ask the team.
