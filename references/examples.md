# Before/after examples

Worked transformations organized by artifact type. Each shows the failure mode, the rewrite, and what changed. Citations marked `[placeholder]` are illustrative; replace with real references before use.

## Docstring

Before:
> """
> This powerful and flexible function provides a robust solution for seamlessly
> handling missing values in your dataset, leveraging a comprehensive suite of
> imputation strategies to enhance data quality.
> """

After:
> """
> Fill missing values in a column.
>
> Parameters
> ----------
> strategy
>     One of 'mean', 'median', or 'most_frequent'.
> """

Changes: cut booster adjectives ("powerful", "flexible", "robust", "seamlessly"), the copula dodge ("provides a solution"), and "leverage"/"enhance". Stated the contract. Omitted types from prose (the signature carries them).

## README usage section

Before:
> In today's fast-paced data landscape, getting started with our blazing-fast,
> production-grade toolkit couldn't be easier. Simply leverage the intuitive CLI
> to seamlessly process your data!

After:
> Process a file from the command line:
>
> ```bash
> plainspeak run data.csv --out clean.csv
> ```

Changes: removed the "in today's landscape" opener, promotional adjectives, "leverage"/"seamlessly", and the exclamation. Led with the task and a runnable command.

## Methods paragraph

Before:
> To carefully investigate the underlying dynamics, samples were meticulously
> incubated, and a robust suite of cutting-edge models was leveraged to thoroughly
> analyze the data.

After:
> Samples were incubated at 37C for 24 hours. We fit negative-binomial GLMs with
> sample-specific offsets using statsmodels (v0.14).

Changes: kept passive voice (conventional in methods) but cut the adverbs ("carefully", "meticulously", "thoroughly") and boosters ("robust", "cutting-edge", "leveraged"). Added the specific temperature, duration, model, and software version that reproducibility requires.

## Results paragraph

Before:
> It was observed that model performance degraded at longer forecast horizons.
> The uncertainty naturally increased as the prediction window expanded. These
> results emerged from our analysis of 54 state-level forecasts.

After:
> We found that performance degraded at longer horizons across all 54 state-level
> forecasts. Each additional week of lead time added roughly 15% to the mean WIS.

Changes: named the actor ("we"), removed false agency ("uncertainty naturally increased", "results emerged"), and replaced the vague claim with a number and the metric (WIS preserved).

## Discussion / limitations

Before:
> It's worth noting that these findings have important implications moving forward.
> Despite these challenges, this work contributes meaningfully to the growing body
> of literature, underscoring the need for continued evaluation.

After:
> Our evaluation covers only two seasons, both with post-COVID influenza dynamics
> that may not generalize. We also lacked a standardized baseline: each forecaster
> chose its own training data, which makes head-to-head comparison difficult.

Changes: cut the filler transition, the "despite these challenges" formula, the vague "implications", and the participle padding. Replaced with two specific limitations and their consequence for the conclusion.

## Abstract

Before:
> In recent years, single-cell RNA sequencing has fundamentally reshaped how we
> think about cellular heterogeneity, marking a pivotal moment in genomics. This
> paradigm shift has far-reaching implications for disease research.

After:
> Single-cell RNA sequencing resolves cell-type-specific expression that bulk
> methods average out. In 12 tumor samples, it identified a resistant subpopulation
> (3% of cells) invisible in matched bulk profiles.

Changes: removed "in recent years", "fundamentally reshaped", "pivotal moment", "paradigm shift", and "far-reaching implications". Replaced with the concrete result and a number.

## Figure caption

Before:
> Figure 3. This striking figure powerfully illustrates the remarkable superiority
> of our model, clearly demonstrating its effectiveness across the board.

After:
> Figure 3. Mean WIS by forecast horizon for each model; lower is better. Error
> bars are 95% bootstrap CIs (1,000 resamples). n = 54 forecasts per horizon.

Changes: cut the editorializing ("striking", "powerfully", "remarkable superiority", "across the board"). Stated what the figure shows, how to read it, and the units, error bars, and n.

## Data dictionary entry

Before:
> temp: An important field that captures temperature information for each
> observation, providing valuable insight into environmental conditions.

After:
> `temp`: float. Air temperature in degrees Celsius. Range -40 to 50. Missing
> coded as NA. Source: on-site sensor, 10-minute mean.

Changes: cut the padding ("important", "valuable insight"). Gave type, units, range, missing-value encoding, and provenance, which is what a data dictionary is for.

## Notebook markdown cell

Before:
> Now let's dive into the really exciting part where the magic happens! We'll
> explore our data and uncover fascinating insights.

After:
> Load the cohort and drop rows missing the primary outcome. Quick distribution
> check before modeling.

Changes: removed the tutorial-voice signposting, "magic", and "fascinating insights". Stated what the next cell does and why in one line.

## Full multi-tell rewrite (general technical)

Before:
> AI-assisted coding serves as an enduring testament to the transformative
> potential of large language models, marking a pivotal moment in the evolution of
> software development. At its core, the value proposition is clear: streamlining
> processes, enhancing collaboration, and fostering alignment. It's not just about
> autocomplete; it's about unlocking creativity at scale.

After:
> AI coding assistants speed up boilerplate: config files, test scaffolding, and
> repetitive refactors. They are weaker on architecture and prone to producing code
> that compiles, passes lint, and still does the wrong thing. Whether they help
> depends on whether you review every suggestion.

Changes: stripped the copula dodge ("serves as a testament"), significance inflation ("pivotal moment", "evolution"), the tricolon ("streamlining, enhancing, fostering"), and the negative parallelism ("not just X, it's Y"). Replaced with specific capabilities, a specific failure mode, and the actual condition for value.
