# SlateSignal Deployment Plan

## 1. Deploy the Node app

Use Render or Railway first.

Build command:

```bash
npm install
```

Start command:

```bash
npm start
```

## 2. Environment Variables

Optional now, useful for deeper data:

```text
THE_ODDS_API_KEY=
OPENAI_API_KEY=
DATABASE_URL=
```

## 3. Persistent Storage

Use a hosted Postgres database when the site needs to keep records across deploys.

Recommended first provider:

- Supabase Postgres

For the current version, the app stores the model record in `pick-log.json`.

## 4. Professional Data Feeds

Recommended upgrades before charging for reports:

- Historical closing odds
- Confirmed lineups
- Weather and park factors
- Bullpen usage and rest
- Scheduled daily result settlement

## 5. Scheduled Updates

Use Render Cron Jobs, Railway cron, GitHub Actions, or a hosted scheduler.

Daily model lean creation:

```bash
curl -X POST https://your-site.com/api/jobs/daily
```

Settle final results:

```bash
curl -X POST https://your-site.com/api/jobs/settle
```

## 6. Real AI Analyst

The endpoint `/api/analyst/chat` is scaffolded. Keep it constrained to supplied matchup data so the AI cannot invent missing stats.
