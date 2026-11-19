# Answer key

The answers for the two exercises that have right answers. Read this after you have tried them.

All of the data is invented for teaching. None of it describes a real company, and the AI finding below is a teaching pattern, not a research result.

## Exercise 1: the CSV lab

Three findings were planted in `pull_requests.csv`. Every number here was recomputed from the file with spreadsheet formulas.

### Finding 1: Platform is the team the average flatters

All four means sit within a quarter of an hour of each other. Platform's median is far lower and its p90 far higher: most of its work is quick, and a growing share waits for days.

| Team | Pull requests | Mean (h) | Median (h) | p90 (h) |
| --- | --- | --- | --- | --- |
| Checkout | 150 | 19.7 | 14.6 | 36.8 |
| Mobile | 206 | 19.7 | 14.8 | 39.4 |
| **Platform** | 150 | 19.6 | **9.2** | **52.2** |
| Search | 144 | 19.8 | 15.2 | 39.2 |

Month by month, Platform's mean never moves while its slow end nearly doubles.

| Platform | Rows | Mean (h) | Median (h) | p90 (h) |
| --- | --- | --- | --- | --- |
| August | 358 to 407 | 19.6 | 15.6 | 36.5 |
| September | 408 to 457 | 19.6 | 9.1 | 52.6 |
| October | 458 to 507 | 19.6 | 5.1 | 69.9 |

Good questions to ask that team: what are the slow ones waiting on, who reviews them, and did something change in September?

### Finding 2: Mobile merges twice as many pull requests, each less than half the size

The count rose 118% in two months while the total code changed stayed flat.

| Mobile | Rows | Pull requests | Median lines | Total lines |
| --- | --- | --- | --- | --- |
| August | 152 to 195 | 44 | 263 | 15,593 |
| September | 196 to 261 | 66 | 171.5 | 15,260 |
| October | 262 to 357 | 96 | 116 | 15,094 |

The other three teams merge the same number every month at a median near 180 lines.

The number alone cannot tell you whether this is good practice or gaming. Smaller pull requests are sound engineering. They are also exactly what gaming a pull-request count looks like. You have to ask the team.

### Finding 3: AI-assisted changes merge faster and fail more often

This was the stretch task.

| | Pull requests | Median cycle time (h) | Failed | Failure rate |
| --- | --- | --- | --- | --- |
| AI-assisted | 250 | 11.2 | 32 | 12.8% |
| Not AI-assisted | 400 | 17.1 | 19 | 4.8% |

The failure rate takes one formula: `=AVERAGEIFS(H2:H651, G2:G651, "yes")`, then the same with `"no"`. The pattern holds inside every team.

The lesson is the pairing. A speed gain reported on its own would have looked like a clear win. Put the failure rate beside it and the picture changes.

## Exercise 2: the anti-pattern clinic

Most scenarios show more than one anti-pattern, so any answer you can defend is fine. The first one listed is the best fit.

| Card | Anti-pattern | How it gets gamed within 90 days | A tension metric that would catch it |
| --- | --- | --- | --- |
| **A. The leaderboard:** pull requests merged per engineer, top five named at all-hands | Individual measurement, also a target turned into a goal | Work is split into more, smaller pull requests. Reviews get rubber-stamped. People avoid hard problems, reviewing and mentoring, which earn nothing. | Report at team level only, then pair the count with rework or change fail rate. Review turnaround shows whether helping others has stopped. |
| **B. 95% adoption:** "AI rollout: success" a month before renewal | Vanity metric: usage standing in for outcome | Managers ask everyone to open the tool once a week. Seats assigned get counted as seats used. Nobody checks what changed in delivery. | Pick an outcome first: cycle time before and after, paired with change fail rate. Add what developers say about the tool. |
| **C. Double the deploys:** a quarterly objective tied to the bonus pool | Target turned into a goal | Releases are cut into smaller deploys. Config-only and no-op changes ship to raise the count. Tests and review are skipped to go faster. | Change fail rate and deployment rework rate. Either one rising while deploys double means the target is being met the lazy way. |
| **D. The velocity table:** story points compared across six teams | Cross-team comparison | Estimates inflate. Stories are split to score more points. Teams pick easy work and stop helping each other. | Stop the comparison: each team reads its own trend. Pair velocity with escaped defects, or with cycle time for finished work. |

One follow-up for every answer: could your tension metric itself be gamed?
