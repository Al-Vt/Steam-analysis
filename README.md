# Steam Analysis

A descriptive analysis of the Steam gaming platform, framed as a hypothetical recommendation report for Ubisoft. The goal: identify what kind of game profile would maximize Ubisoft's chances of breaking through on a platform with 50,000+ titles.

Built with PySpark on Databricks as part of the Jedha Big Data module.

## What the analysis answers

The notebook is structured around three layers of questions:

**Macro-level**: Which publishers dominate the platform? How are prices distributed? What languages are required? Did COVID actually change release patterns?

**Genre-level**: Which genres are most common, most reviewed, most profitable? Do big publishers favor specific genres? Is there a gap between what's released and what players actually engage with?

**Platform-level**: Windows vs Mac vs Linux — what's the actual breakdown, and does it depend on genre?

## Key findings

A few things stood out:

- **The indie genre dominates the catalog (71% of games).** Steam is essentially a small-studio platform by volume.
- **But Action is the genre that wins.** It accounts for 25% of all positive reviews and is by far the most lucrative genre estimated from owner counts × price.
- **Casual games are a paradox.** Released in massive quantities by the top publishers (Big Fish Games, 8floor), but barely reviewed — players use them but don't engage enough to leave feedback.
- **Pricing is concentrated low.** Most games sell between $0 and $10. Discounts are rare (4.5% of games) but aggressive when they happen (57% off on average).
- **Windows is non-negotiable.** ~99% of games run on it. Mac sits at 22%, Linux at 15%.
- **Steam is for everyone.** 98.8% of games have no age restriction.
- **COVID had a clear impact.** Release counts spiked in 2020-2021 with 8,000+ games per year, on top of an existing growth curve that aligned with the global rollout of fiber internet.

## Recommendation for Ubisoft

If the goal is to maximize visibility on Steam given current dynamics:

- Target a price point between $5 and $20
- No age restriction
- English required, with German, French, Russian, Chinese, Spanish as secondary options
- Windows-only is fine; Mac/Linux ports only worth it if the engine handles them automatically (Unity, Unreal)
- Genre: action-adventure. Action wins on engagement and revenue, adventure has a strong positive review ratio relative to its market share, and combining the two avoids head-on competition with the indie-dominated single-genre segments
- Strong artistic direction is critical — the main competition is 35,000+ indie games, so a generic AAA aesthetic won't cut through

## Method notes

A few things worth being upfront about:

- **Sales data isn't in the dataset.** Revenue estimates use owner counts × price, which is a proxy, not actual revenue. The relative ranking between genres should be reliable; the absolute numbers shouldn't be trusted.
- **Review ratios are a popularity proxy.** Without sales data, total reviews (positive + negative) are the best signal we have for engagement. This biases toward games that generate strong reactions.
- **Outlier handling was minimal.** Some prices in the raw data were stored in dollars instead of cents (66 outliers out of 55,691 entries) and some `required_age` values were clearly wrong (35, 180). These were filtered but not investigated further.
- **Publisher counts probably overstate small studios.** Some publisher names appear with thousands of releases that look more like aggregator activity than traditional publishing.

## Environment

This notebook was developed on **Databricks Community Edition** with PySpark. Two consequences for anyone trying to reproduce it:

- The `display()` calls used throughout are Databricks-specific. In a standard Jupyter setup, you'd need to replace them with `df.show()` or `df.toPandas()`.
- The dataset is loaded from a Jedha-hosted S3 bucket (`s3://full-stack-bigdata-datasets/Big_Data/Project_Steam/steam_game_output.json`) which isn't publicly accessible. To re-run the analysis you'd need to source a similar Steam dataset (the one on Kaggle by Nik Davis is the closest equivalent) and adjust the read path.

## Stack

PySpark, Spark SQL, Databricks. Versions in `requirements.txt`.

## Dataset

Source: Jedha-modified version of a public Steam dataset, originally compiled from the Steam API. Approximately 55,000 entries covering games and other software available on the platform.
