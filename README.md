# Steam Analysis

This project is based on the use of Steam’s dataset relating to its platform. Steam is the most popular online gaming platform on the market, with over 50,000 games available on its platform in the year this dataset was published.

We will therefore carry out a descriptive analysis simulation for Ubisoft, in order to determine the typical profile of games we would recommend they produce.

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

## Environment

This notebook was developed on Databricks Community Edition with PySpark. Two consequences for anyone trying to reproduce it:

The entire notebook is available here: https://dbc-b50ed537-d463.cloud.databricks.com/editor/notebooks/2256538333767863?o=2274689051990487

## Stack

PySpark, Spark SQL, Databricks. Versions in `requirements.txt`.

## Dataset

Source: Jedha modified version of a public Steam dataset, originally compiled from the Steam API. Approximately 55,000 entries covering games and other software available on the platform.
