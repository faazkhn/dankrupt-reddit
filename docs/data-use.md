# Data use

This page lists every piece of Reddit data Dankrupt plans to request, what happens to it, and what is kept.

## Scope

- **Subreddits:** a fixed, operator-curated list of public meme subreddits (starting with r/memes, r/dankmemes and r/MemeEconomy). No private, quarantined or NSFW subreddits.
- **Memes:** each listed meme has a few search terms, such as "moo deng". There are about 30 to 50 listed memes at a time.
- **Content:** public posts and comment counts only.

## Requests

Once an hour, for each listed meme:

1. Search the curated subreddits for posts matching the meme's terms, sorted by new, limited to the past hour.
2. Count the matching posts and add up their comment counts.

That is roughly 50 requests an hour in total, far below Reddit's published limit of 100 queries per minute. Requests are authenticated with OAuth and use a descriptive User-Agent that names the app and links to this repository. Quota use is logged.

## Processing

API responses are read in memory, reduced to two numbers per meme per hour (new posts and new comments), and discarded. Nothing else from the response is written anywhere: no post IDs, titles, bodies, links, usernames or user IDs.

## Storage and retention

| Kept | Not kept |
| --- | --- |
| `meme, hour, post_count, comment_count` | Post or comment text, titles, URLs, IDs |
| | Usernames, user IDs, avatars, flair |
| | Raw API responses |

Counts are kept while the meme is listed and are deleted if Reddit asks, or if Reddit's terms require a shorter retention period. Players never see Reddit counts directly. They see a combined attention score built from several sources.

## Uses we rule out

Dankrupt does not use Reddit data for advertising, profiling, surveillance, resale, or training AI or machine-learning models, and does not combine it with data about individual Redditors. Dankrupt is non-commercial. Any future monetisation would first need Reddit's written approval.
