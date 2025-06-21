
---

## Real-World SQL in a Data Pipeline (Sakila Example)

Let’s take a peek at how SQL fits into the life of a data engineer — using our trusty Sakila database.

Imagine this:

> You’re a junior data engineer at **SakilaFlix**, and your team needs a daily report showing how many rentals happened yesterday, which films were most popular, and how much revenue came in.

Your job is to **write the SQL** that powers that report.

It might look like this:

```sql
SELECT
  DATE(rental_date) AS rental_day,
  COUNT(rental_id) AS total_rentals,
  SUM(payment.amount) AS total_revenue
FROM
  rental
JOIN
  payment ON rental.rental_id = payment.rental_id
WHERE
  DATE(rental_date) = DATE('now', '-1 day')
GROUP BY
  rental_day;
```

That’s it — you just wrote the brain behind a data pipeline.

Later, your team might plug this query into a **script**, **dashboard**, or schedule it to run automatically.

But what controls *when* and *how often* this SQL runs?

---

## What Is Orchestration?

Think of orchestration as a way to **manage the timing and flow** of different data tasks — like a conductor guiding a symphony.

Let’s say your data pipeline involves:

* Fetching raw data from an API
* Cleaning and transforming it with SQL
* Saving the results to a dashboard

You want all of that to happen:

* In the right order
* At a scheduled time (like every morning)
* With error checks (so you know if something breaks)

That’s what orchestration tools do.

They **don’t replace SQL** — they run your SQL at the right time and make sure everything works smoothly.

---

## A Glimpse of What’s Ahead

Here are a few orchestration tools you’ll learn later in this course:

* **Airflow:** Great for running SQL or Python scripts on a schedule
* **dbt:** Focused entirely on SQL-based data transformations
* **Dagster:** Modern tool for combining SQL, Python, and monitoring

You don’t need to learn these now — just know that **the SQL you’re writing today will plug into these tools later**.

You’re laying the foundation for the pipelines you’ll build.

---

## Try This Out!

Here are a few SQL-only challenges using the Sakila database. You don’t need to build any pipelines yet — just focus on writing the queries a pipeline would use.

1. **How many rentals were made each day over the past week?**

   * Use the `rental` table and group by date

2. **Which 5 films were rented the most in the last 30 days?**

   * Use `rental`, `inventory`, and `film` tables

3. **Show total revenue per store.**

   * Use `payment`, `staff`, and `store` tables

4. **Find all customers who rented more than 3 times last month.**

   * Use `rental` and `customer`

5. **Design your own report!**

   * Pick a business question (like “Which film category earns the most?”)
   * Write the query that answers it

You will learn how to schedule and automate it later.

---
