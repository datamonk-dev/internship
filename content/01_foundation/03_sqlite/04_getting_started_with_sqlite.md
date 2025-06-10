
---

# SQLite Getting Started – Let’s Play with Real Data 🎬

Ready to roll up your sleeves and *actually use* SQLite? This time, we’re going beyond just reading—we’re going to **run commands**, **inspect a real database**, and **get hands-on**.

---

## Meet Sakila – Your First Real-World Database

A sample database called **Sakila**. Think of it like a miniature movie rental store—complete with tables for films, actors, customers, payments, and more.

It’s small, fun, and realistic—just right for learning how databases really work.

---

## Step 1: Download the Sakila Database

You’ll first need to get the `.db` file for Sakila. Luckily, many kind souls have shared prebuilt SQLite versions of it.

 Here’s one place to download it directly:
 [Sakila SQLite Download (GitHub)](https://github.com/ivanceras/sakila/blob/master/sqlite-sakila-db/sakila.db)

> Right-click “Raw” → “Save Link As” to save it as `sakila.db`

Once downloaded, open it using your terminal or command line and make sure you are in the same directory where it is saved:

```bash
sqlite3 sakila.db
```

And here you go! Welcome to the SQLite shell. Now unleash you hidden sql power and do whatever you want with all this data.

---

## 🔍 Step 2: Poke Around a Little

Also explore.

### See the Schema

```sql
.schema
```

This shows how the tables were created. It’s like reading the blueprint of the database.

---

### Export Movie Data to CSV

Let’s say you want to send your boss a CSV file of best-selling movies. Try to make the query for this and then:

```sql
.mode csv
.headers on
.output movies.csv
SELECT * FROM film;  -- write your query here for best-selling movies --
.output stdout
```

That's it! You just created a real CSV file called `movies.csv`. You can open it in Excel, Google Sheets, or even VS Code and look around.

 The `.mode` command changes the output format.
 `.headers on` includes column names in the CSV.
 `.output` lets you choose where to send the output.


---

### Try the `.explain` Command

Want to know how SQLite actually *executes* your SQL query?

```sql
.explain
SELECT * FROM film WHERE rating = 'PG';
```

This gives you a peek into the query planner—the behind-the-scenes logic of how your query is run. Don’t worry if it looks complex right now; just knowing it's there is a solid start.

---

### Done for the Day? Use `.exit`

When you're finished exploring:

```sql
.exit
```

And just like that, you’ve closed the SQLite shell.

---

## Summary – What You Learned

By now, you’ve:

* Opened a real database (`sakila.db`)
* Explored the schema with `.schema`
* Exported data using `.mode`, `.headers`, and `.output`
* Peeked under the hood with `.explain`
* Cleanly exited with `.exit`

---

## Need More?

Then Try experimenting with other queries too:

* `SELECT title, release_year FROM film WHERE length > 120;`
* `SELECT COUNT(*) FROM customer;`
* `SELECT first_name, last_name FROM actor LIMIT 10;`

And if anything looks weird or confusing—**that’s okay**. You’re building muscle memory, and every command brings you one step closer to confidence.

---
