# World Cup Database Project

A PostgreSQL-based project to analyze FIFA World Cup match data. This project allows for data insertion, processing, and insightful queries on tournament statistics.

## Table of Contents

- [About the Project](#about-the-project)
- [Files Included](#files-included)
- [Database Schema](#database-schema)
- [Getting Started](#getting-started)
  - [Setup the Database](#setup-the-database)
  - [Insert Data](#insert-data)
  - [Run Queries](#run-queries)
- [Queries Overview](#queries-overview)
- [License](#license)

---

## About the Project

This project demonstrates how to:
- Use SQL to define and manage a relational database for FIFA World Cup data.
- Populate a database using Bash scripts.
- Execute queries to analyze team and match performance.

---

## Files Included

### 1. **`games.csv`**
A CSV file containing match data with the following columns:
- `year`: Year of the match.
- `round`: Tournament round (e.g., Final, Semifinal).
- `winner`: Winning team.
- `opponent`: Opponent team.
- `winner_goals`: Goals scored by the winning team.
- `opponent_goals`: Goals scored by the opponent team.

### 2. **`worldcup.sql`**
SQL file defining the database schema for the project.

### 3. **`insert_data.sh`**
A Bash script to:
- Populate the database from `games.csv`.
- Handle team insertion without duplication.
- Add match records to the database.

### 4. **`queries.sh`**
A Bash script containing SQL queries for analyzing the database.

---

## Database Schema

### Tables
- **`teams`**
  - `team_id`: Primary key.
  - `name`: Team name.

- **`games`**
  - `game_id`: Primary key.
  - `year`: Year of the match.
  - `round`: Tournament round.
  - `winner_id`: Foreign key referencing `teams.team_id` (winner).
  - `opponent_id`: Foreign key referencing `teams.team_id` (opponent).
  - `winner_goals`: Goals scored by the winning team.
  - `opponent_goals`: Goals scored by the opponent team.

---

## Getting Started

### Prerequisites
- PostgreSQL installed on your system.
- Basic knowledge of Bash scripting and SQL.

### Setup the Database
Run the following command to create the database schema:
```bash
psql --username=postgres --dbname=worldcup < worldcup.sql

### Insert Data
Use the insert_data.sh script to populate the database:
```bash
bash insert_data.sh
For testing, you can use:
```bash
./insert_data.sh test

### Run Queries
Execute queries.sh to retrieve insights from the database:
```bash
./queries.sh

---

## Queries Overview
The queries.sh script includes:
- Total number of goals by winning teams.
- Total goals scored by both teams in all games.
- Average number of goals scored by winning teams.
- Most goals scored by a team in a single game.
- Number of games where the winning team scored more than 2 goals.
- Winner of the 2018 World Cup.
- Teams that participated in the 2014 "Eighth-Final."
- List of unique winning teams.
- Champions for each year.
- Teams whose names start with "Co."
