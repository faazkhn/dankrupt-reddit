# Architecture

## Today

Dankrupt is a web game. One always-on server runs the exchange: an order book and matching engine, price updates every 100 ms, and an event log in Postgres that can replay the market exactly. Each meme's fair value comes from attention signals. Wikipedia pageviews are live now, and in-game page views and watchlists are also counted.

## Where Reddit fits

```
Reddit API ──hourly──▶ attention ingest ──counts only──▶ fair value ──▶ house quotes ──▶ players
```

The Reddit ingest is a scheduled job next to the existing Wikipedia ingest. It only produces the two hourly counts described in [data use](data-use.md). If Reddit data is missing for two polls in a row, the game marks the source stale and leans on the other sources. Prices never depend on Reddit alone.

## Reddit Developer Platform (Devvit)

We would like Dankrupt to be playable on Reddit itself eventually, and are open to doing the data side through Devvit now if that is Reddit's preferred route. A Devvit version would look like this:

- A Devvit app installed on Dankrupt's own subreddit, using the scheduler to compute the same hourly counts through the in-platform Reddit API.
- The game server pulling those counts through an External Endpoint, rather than the app sending data off-platform.

Two things are uncertain for this path today:

1. The exchange needs one shared market across all players, which lives on our server. A Devvit app would need External Endpoints (limited access) or HTTP Fetch to our own domain.
2. The counts span several public subreddits where our app is not installed, so cross-subreddit read access would be needed.

A playable Devvit version of the game (an interactive post showing a meme's chart and letting Redditors trade) is a later goal. It is not part of this request.
