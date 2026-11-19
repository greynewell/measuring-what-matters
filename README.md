# Measuring What Matters

**Building a developer productivity program engineers can trust.**

Materials for the three-hour workshop at [QCon San Francisco](https://qconsf.com/training/nov2026/measuring-what-matters-building-developer-productivity-program-engineers-can-trust), November 19, 2026, led by Grey Newell.

Most teams measure productivity. Few trust the numbers. This workshop is about closing that gap: choosing a small set of metrics, reading them properly, and rolling them out without teaching people to game them.

## In the room? Start here

1. Download [`pull_requests.csv`](pull_requests.csv). On its page, use the download button at the top right.
2. Open it in a spreadsheet. Excel, Google Sheets and Numbers all work.
3. Sign in to the AI tool you normally use. You will need it after the break.

Want everything at once? [Download all the files as a zip](https://github.com/greynewell/measuring-what-matters/archive/refs/heads/main.zip).

## What you leave with

A starter set you can pilot with one team for 30 days:

- **3 metrics** that answer your own question
- **3 tension metrics**, one for each, to catch gaming
- **1 qualitative signal**: what your people tell you

You build it line by line on the [worksheet](worksheet.pdf) as the morning goes.

## The morning

| Time | Part | What happens |
| --- | --- | --- |
| 9:00 | Opening | The promise, a show of hands and a warm-up |
| 9:20 | Two frameworks | DORA and SPACE, and when to use each |
| 9:35 | Reading the numbers | Median, p90 and **Exercise 1: the CSV lab** |
| 10:15 | When metrics go wrong | Goodhart's law, four anti-patterns, tension metrics |
| 10:30 | Break | |
| 10:45 | Anti-pattern clinic | **Exercise 2**, at your table, with scenario cards |
| 11:05 | People and AI | Sentiment, and measuring AI tools by outcome |
| 11:30 | Rollout and your starter set | Trust, then **Exercise 3: build your starter set** |

## What is in this repository

| File | What it is |
| --- | --- |
| [`pull_requests.csv`](pull_requests.csv) | The dataset for Exercise 1 |
| [`worksheet.pdf`](worksheet.pdf) | The two-page worksheet you fill in through the morning |
| [`scenario-cards.pdf`](scenario-cards.pdf) | The four scenario cards for Exercise 2 |
| [`starter-set.md`](starter-set.md) | The worksheet as a fill-in text file, for laptops and AI agents |
| [`handout.pdf`](handout.pdf) | Terms and explainers, with a glossary and sources |
| [`slides.pdf`](slides.pdf) | The slides |
| [`AGENTS.md`](AGENTS.md) | The workshop explained to an AI agent, with ground rules for metric advice |
| [`.claude/skills/`](.claude/skills) | Three agent skills: the three questions, DORA and SPACE |

## Working with an AI agent

Clone this repository and open it in a coding agent. [`AGENTS.md`](AGENTS.md) tells the agent what the workshop is, what the dataset holds and how to help without handing you a dashboard. Three skills go with it:

| Skill | What it does |
| --- | --- |
| [`three-questions`](.claude/skills/three-questions/SKILL.md) | Interrogates any metric: what it hides, what it rewards, what counter-balances it |
| [`dora-metrics`](.claude/skills/dora-metrics/SKILL.md) | Explains and critiques the five DORA delivery metrics |
| [`space-framework`](.claude/skills/space-framework/SKILL.md) | Audits a set of metrics for balance across the five SPACE dimensions |

Try it on your starter set: ask the agent to run the three questions on each metric you chose.

## The AI harness exercise

Two rounds, after the break. The point is to see how much the answer depends on what you bring to the tool.

**Round 1.** Open a fresh chat in your AI tool, outside this repository, and send exactly this:

```
Suggest five metrics to prove that our AI coding assistant is paying off.
```

**Round 2.** Ask again, one of two ways, then compare with your neighbor.

- **By hand.** Rewrite the prompt so it asks the three questions of every metric: what does it hide, what behavior does it reward, what counter-balances it.
- **With the skill.** Send the same Round 1 prompt, unchanged, with the [`three-questions`](.claude/skills/three-questions/SKILL.md) skill loaded. Open this repository in a coding agent, or paste the skill file into your chat first.

Same tool, different results.

## The lab dataset

`pull_requests.csv` holds 650 pull requests from four teams, merged from August to October 2026. **The data is invented for teaching.** It does not describe any real company.

| Column | Name | What it holds |
| --- | --- | --- |
| A | `pr_id` | A unique number for each pull request |
| B | `team` | Checkout, Mobile, Platform or Search |
| C | `merged_date` | The day it merged |
| D | `month` | 8, 9 or 10 |
| E | `cycle_time_hours` | Hours from opened to merged |
| F | `lines_changed` | Lines added plus lines removed |
| G | `ai_assisted` | yes or no |
| H | `change_failed` | 1 if it led to a rollback, hotfix or incident, otherwise 0 |

Rows are sorted by team, so each team is one block of rows and you do not need to filter.

| Team | Cycle time cells |
| --- | --- |
| Checkout | `E2:E151` |
| Mobile | `E152:E357` |
| Platform | `E358:E507` |
| Search | `E508:E651` |

The three formulas, shown here for Checkout:

```
=AVERAGE(E2:E151)
=MEDIAN(E2:E151)
=PERCENTILE(E2:E151, 0.9)
```

**Your task:** work out the mean, median and p90 for each team, find the team the average flatters, and write one question you would ask that team. If you finish early, compare the AI-assisted changes with the rest using columns G and H.

## Cheat sheet

### The three questions

Ask these of any metric before you trust it.

1. **What does it hide?**
2. **What behavior does it reward?**
3. **What counter-balances it?**

### DORA: five metrics for delivery

DORA (DevOps Research and Assessment) is a long-running research program. Its metrics measure how well software gets delivered.

| Group | Metric | Plain meaning |
| --- | --- | --- |
| Throughput | Change lead time | From committed code to running in production |
| Throughput | Deployment frequency | How often you deploy |
| Throughput | Failed deployment recovery time | How long it takes to recover when a deployment fails |
| Instability | Change fail rate | Share of deployments that need immediate intervention |
| Instability | Deployment rework rate | Share of deployments that are unplanned fixes for an incident |

Its clock starts at the commit, so it sees nothing before that, and it says nothing about how the work feels.

### SPACE: five dimensions to cover

SPACE is a checklist, not a set of metrics. It names what to cover and leaves the choice of measures to you.

| | Dimension | Plain meaning |
| --- | --- | --- |
| **S** | Satisfaction and well-being | How fulfilled and healthy developers are |
| **P** | Performance | Outcomes, as opposed to output |
| **A** | Activity | Counts of things done |
| **C** | Communication and collaboration | How well people work together |
| **E** | Efficiency and flow | Progress without interruption or delay |

### Which one?

| Your question | Start with |
| --- | --- |
| Is our delivery healthy, and is it improving? | DORA |
| Are we measuring productivity in a balanced way? | SPACE, with DORA metrics filling some of its slots |

### Read the median and the p90, not the average

Time-based data is rarely bell-shaped: most items are quick and a few are very slow. The **median** tells you the typical case. The **p90** tells you the slow end, where one item in ten waits at least that long. An average can stay flat while the typical case gets faster and the slow end gets slower.

### Four anti-patterns

| Anti-pattern | What it looks like |
| --- | --- |
| Vanity metric | A number that looks good and changes no decision: lines of code, commit counts, tool adoption |
| Target turned into a goal | "Double deployment frequency" written as an OKR |
| Individual measurement | A leaderboard of pull requests merged per engineer |
| Cross-team comparison | Teams ranked by velocity |

### Tension metrics

A tension metric is a second measure chosen because it gets worse when the first one is gamed. To find one, ask: **if someone hit this number the lazy way, what would get worse?** Measure that.

| Primary metric | Tension metric |
| --- | --- |
| Deployment frequency | Change fail rate |
| Cycle time | Rework |

### Measuring AI tools

Adoption, acceptance rate and lines generated show that a tool is being used. They do not show that it is paying off. Choose the outcome first, record a baseline, compare before and after, pair the outcome with a tension metric, and ask the people using it.

### Five rollout habits

1. Report at team level, never the individual.
2. Show the people measured their own data first.
3. Write down what the data will never be used for.
4. Pilot with one team before going wider.
5. Retire metrics that stop helping.

## Your first week back

- [ ] Show your team the starter set and ask what it hides.
- [ ] Agree what the numbers will never be used for, and write it down.
- [ ] Pick the pilot team and a review date 30 days out.

## Further reading

- [DORA's software delivery performance metrics](https://dora.dev/guides/dora-metrics/), DORA
- [The SPACE of Developer Productivity](https://queue.acm.org/detail.cfm?id=3454124), ACM Queue, 2021
- [State of AI-assisted Software Development 2025](https://services.google.com/fh/files/misc/2025_state_of_ai_assisted_software_development.pdf), DORA
- [Beware What You Measure: The Principle of Pairing Indicators](https://blog.holistics.io/blog/beware-what-you-measure-the-principle-of-pairing-indicators/), Holistics, on Andy Grove's paired indicators
- [Psychological safety: definition and key references](https://psychiatry.ucsd.edu/research/programs-centers/instep/tools-resource/definitions/emergent-states/affective-emergent-states/psych-safety.html), UC San Diego

The [handout](handout.pdf) explains each of these in more depth.

## License

These materials are licensed under [Creative Commons Attribution 4.0](https://creativecommons.org/licenses/by/4.0/). Use them, adapt them and teach with them, as long as you credit Grey Newell and link back here. See [`LICENSE`](LICENSE).
