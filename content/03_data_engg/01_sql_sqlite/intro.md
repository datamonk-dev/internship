
---

# Using SQL & SQLite in Data Engineering

Now that you're stepping into the world of data engineering, it's time to meet one of the most practical and powerful tools you'll use on the job: **SQL**. But don’t worry—we’re not going to teach SQL from scratch here. There are already tons of great tutorials for that (and we’ll link you to a few!).

Instead, this is all about **how** SQL—and especially **SQLite**—fits into the data engineering toolkit.

---

## Why SQL Still Matters (Yes, Even in 2025)

SQL might be decades old, but it’s still *everywhere* in the data world. And for good reason:

* It’s the universal language for querying structured data.
* It works beautifully for transforming raw data into usable form.
* It’s at the heart of many analytics dashboards, ETL pipelines, and even machine learning prep work.

In short: if your job involves touching data (hint: it will!), you’ll use SQL.

> Even the fanciest AI model in the world probably starts with a simple SQL query pulling cleaned data from a warehouse.

---

## Why SQLite?

You’ll probably encounter **PostgreSQL**, **BigQuery**, or **Snowflake** in production—but **SQLite** is still a *gem* for learning, prototyping, and local testing.

Think of it as a **tiny, zero-fuss database** that lives in a file on your computer. You can:

* Use it to test ETL scripts locally
* Quickly explore datasets (like `.db` files from Kaggle or open data portals)
* Load results into charts or visualizations
* Run simple pipelines for data transformation

All **without spinning up any servers** or writing configs.

---

## SQL for Analysis & Visualization

As a data engineer, you’re not just writing SQL to retrieve data—you’re shaping it for:

* Reporting
* Dashboards (like Metabase, Superset, Looker, etc.)
* Feeding data to plotting libraries (`matplotlib`, `seaborn`, `plotly`)
* Creating materialized views for downstream teams

You’ll often use SQL queries to generate **aggregates, time series, or joins**, then visualize them in Python or pass them to an analyst or ML pipeline.

> TL;DR: SQL is the prep kitchen before the data gets plated and served 🍽️

---

## SQLite Extensions You Should Know

SQLite is compact, but surprisingly flexible—thanks to its **extension system**. These allow you to do way more than just basic SELECTs.

Here are some commonly used ones in data workflows:

### `json1`

Work with JSON data directly inside SQLite tables.

```sql
SELECT json_extract(data, '$.user.name') FROM logs;
```

Great when dealing with semi-structured data from APIs or logs.

### `fts5` (Full Text Search)

Adds blazing-fast full-text search across columns.

Use it to search product names, articles, comments, etc.

```sql
SELECT * FROM documents WHERE content MATCH 'machine learning';
```

### `Rtree`

Efficiently indexes and queries spatial or range-based data (like coordinates or bounding boxes).

Handy for anything geospatial or involving shapes.

### `sqlite-vss`

A newer extension for **vector similarity search**.
Used in AI/ML workflows—for example, searching through embeddings.

---

### Heads-up: SQLite Has Limits

As cool as these extensions are, keep in mind:

* They’re *not* as feature-rich as dedicated tools (e.g., PostGIS, Elasticsearch, Pinecone).
* SQLite isn’t built for high-concurrency, multi-user environments.
* You probably *won’t* use SQLite in production pipelines—but it’s great for local testing, prototyping, and learning.

That said: **understanding these tools will make you a better data engineer**—even when you switch to PostgreSQL or Snowflake later.

---

## Resources to Learn SQL (If You Need a Refresher)

If you're not super comfortable with SQL yet, don't worry! You can learn it alongside this course.

Here are a few solid, beginner-friendly resources:

* [Mode SQL Tutorial](https://mode.com/sql-tutorial/)
* [SQLBolt](https://sqlbolt.com/)
* [SQLite Docs](https://www.sqlite.org/docs.html)

---