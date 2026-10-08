# ⚽ World Cup Database

A relational database built with **PostgreSQL** and **Bash**, turning raw World Cup match data (the final three rounds of the 2014 and 2018 tournaments) into clean, queryable tables.

Built as part of the [freeCodeCamp Relational Database certification](https://www.freecodecamp.org/).

## 🎯 The problem

Match results arrive as one flat CSV where team names repeat on every row. That makes it hard to count, compare or trust the data. This project splits it into related tables and automates the loading, so questions like "who won each tournament?" or "how many goals per game on average?" can be answered with one query.

## 🗂️ Database design

| Table | Columns |
|-------|---------|
| `teams` | `team_id` (PK), `name` (UNIQUE) |
| `games` | `game_id` (PK), `year`, `round`, `winner_id` (FK), `opponent_id` (FK), `winner_goals`, `opponent_goals` |

- Every column is `NOT NULL`
- `winner_id` and `opponent_id` both reference `teams(team_id)`
- Result: **24 teams** and **32 games**

## 📁 Files

| File | What it does |
|------|--------------|
| `worldcup.sql` | Full dump to rebuild the database |
| `insert_data.sh` | Reads `games.csv` and loads teams and games with no duplicate teams and no hard-coded IDs |
| `queries.sh` | Runs 12 reporting queries |

## 📊 Questions the queries answer

- Total and average goals per game
- Most goals scored by one team in a game
- Games where the winner scored more than 2 goals
- Winner of the 2018 tournament
- Teams that played in the 2014 Eighth-Final round
- Every champion by year
- Teams whose names start with "Co"

## 🚀 Run it yourself

```bash
# rebuild the database
psql -U postgres < worldcup.sql

# run the reports
chmod +x queries.sh
./queries.sh
```

## 🛠️ Skills practised

Schema design · Primary and foreign keys · Joins · Aggregate functions · Shell scripting · Data loading without duplicates

## 💡 Where this applies

The same pattern (flat file → normalized tables → automated load → reports) is how you would build a school results system, a payments ledger or a patient-visit database.

---
👤 **Uti Wisdom** · Data Engineer in training · [GitHub](https://github.com/utiwisdom) · [LinkedIn](https://linkedin.com/in/uti-wisdom-286602228/)
