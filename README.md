# Dankrupt Exchange · Reddit integration

Dankrupt Exchange is a free, non-commercial web game: a paper-money stock exchange where the listed companies are internet memes. Players trade play coins that can never be bought, sold or cashed out. Each meme's "fair value" follows how much attention it is getting on the internet.

This repository covers the Reddit side of Dankrupt only. It holds documentation, and no code yet. Code will be added here, in the open, once Reddit approves access.

## What we want to do with Reddit

Count, once an hour, how many new posts and comments mention each listed meme in a small set of public meme subreddits, such as r/memes, r/dankmemes and r/MemeEconomy. Those hourly counts become one input to the meme's fair value, alongside Wikipedia pageviews and in-game activity.

That is the whole use. We read public listings. We do not post, comment, vote, message or moderate.

## What we never do

- Store or show post titles, post bodies, comments, usernames or user IDs. Only numbers are kept.
- Profile, track or contact any Redditor.
- Sell, license or share Reddit data, or use it to train AI or machine-learning models.
- Make money from Reddit data. Dankrupt has no ads, no payments and no paid features. If that ever changes, we will ask Reddit for written approval first.
- Scrape. All access goes through Reddit's official APIs, within the rate limits Reddit sets.

## Docs

- [Data use](docs/data-use.md): exactly what is requested, what is kept and for how long
- [Architecture](docs/architecture.md): how the counts flow into the game, and the plan for a Reddit Developer Platform (Devvit) version
- [Privacy](docs/privacy.md): the Reddit-related part of Dankrupt's privacy policy

## Status

| Step | State |
| --- | --- |
| App registered with Reddit | Submitted, November 2026 |
| Reddit approval | Waiting |
| Integration code | Not started. Nothing calls Reddit today. |

## Contact

Open an issue in this repository, or message the Dankrupt account on Reddit.
