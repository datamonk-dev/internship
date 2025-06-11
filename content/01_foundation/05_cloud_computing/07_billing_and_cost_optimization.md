
---

# AWS Billing—Avoiding Expensive Surprises

Welcome to the “rookies world” of cloud billing—yes, things can get expensive if you’re not careful.

---

## Horror Stories & Wise Moves by Big Names

Plenty of developers accidentally leave resources running, only to return from vacation and find massive bills. Even big companies have had their learning moments:

* **Ahrefs** — an SEO tools company — built their $400M search engine on bare-metal servers, calling cloud pricing “an expensive trap.” A bold example of scaling without the cloud.
* **Dropbox** famously built their own storage infrastructure after estimating they’d save hundreds of millions compared to staying on AWS.

The lesson? Even at scale, cloud costs can escalate fast—and real savings can come from careful planning and a bit of old-school infrastructure work.

---

## AWS’S Pay–Per–Use Model is Tricky

Your cloud bill could include separate charges for:

* EC2 compute time
* EBS volumes and snapshots
* Data transfer
* Elastic IPs
* CloudWatch logs and metrics
* NAT gateways, load balancers, etc.

One service could explode into **10+ line items**, and you’re billed not just for *what* you use, but *how long*, *how much*, and *how often*.

---

## Always Shut Down Unused Resources

Here’s your golden rule:

> If you don’t need it right now, **delete it** or **stop it**.

Pro tips:

* Terminate test EC2 instances when done.
* Detach or delete unused EBS volumes.
* Release unattached Elastic IPs.
* Remove idle NAT Gateways and CloudWatch log groups.
* Script these cleanups if possible—automation saves your wallet.

---

## Billing Alerts—Your Cloud Watchdog

Never blindly trust your dashboard. Instead:

1. Visit the **Billing Dashboard** in AWS.
2. Set a threshold (e.g., ₹50 or ₹100).
3. Receive email alerts the moment you're near the limit.

This simple step can save you from those dreaded ₹50,000 wake-up calls.

---

## Quick Exercise

Try this: (and do not worry it will not cost more than your cold coffee)

1. Set a billing alarm at a threshold you’re comfortable with.
2. Spin up an EC2 instance.
3. Observe your Billing Dashboard as it runs.
4. Generate logs or upload files and watch the charges.
5. Terminate everything and check that your usage stops.
6. Bonus: Explore Cost Explorer to find your biggest spenders.

---
