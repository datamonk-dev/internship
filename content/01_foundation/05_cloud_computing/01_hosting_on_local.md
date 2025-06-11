
---

# Teaser Task: “Why Can’t My Phone Access My Local Python Server?”

Let’s do a little magic trick—except this one might *fail* on purpose… and that’s exactly the point.

---

## Your Mission (If You Choose to Accept It):

1. Open your laptop (or any computer) and run this in your terminal:

   ```bash
   python3 -m http.server 3000
   ```

2. On that same laptop, open your browser and visit:

   ```
   http://localhost:3000
   ```

   Yay! You’ll see a directory listing or your files—success!

3. Now grab your mobile phone, make sure it’s connected to **the same Wi-Fi**, and type in:

   ```
   http://<your-laptop-ip>:3000
   ```

   (You can find your laptop’s IP using `ifconfig` on Linux/macOS or `ipconfig` on Windows.)

4. Boom! It works. Your phone sees the server running on your laptop.

5. Now the twist:
   **Turn off Wi-Fi on your phone and switch to mobile data (4G/5G)**. Try accessing it again.

   ```
   http://<your-laptop-ip>:3000
   ```

   Uh-oh. Doesn’t work.

---

## What Just Happened?

You didn’t break the internet—promise. Let’s walk through **why this happened** in a friendly way.

---

## Local IP vs Public IP: Know the Difference

When your devices (laptop and phone) are on the same Wi-Fi, they’re part of the same **local network**—think of it like all your roommates hanging out in the same apartment.
They can talk to each other using **local IP addresses** like `192.168.x.x` or `10.x.x.x`.

But when your phone switches to **mobile data**, it’s no longer in your “home network.” It’s out in the wild—using a **different public network**.

Now, it’s like your phone is trying to call your roommate... but doesn’t know your apartment number anymore.

---

## But Wait, What’s Blocking It?

Two main things:

1. **Your local IP address is private**, not visible on the public internet.
2. **Your network is behind something called a NAT (Network Address Translation)**. It keeps internal addresses hidden from the outside world for safety.
3. **Your firewall or router probably isn’t set up** to forward that request from the public internet to your computer. (And that’s a *very* good thing—keeps hackers away.)

---

## Real-World Analogy: Pizza Delivery Again?

Imagine you’re ordering pizza (yes, again 🍕). If you're inside the building (local network), the pizza guy finds your door easily.

But if you're outside the city (mobile data) and only know the building's name (public IP), you still can't reach the exact apartment (your computer) unless there's a doorman (router) forwarding you to the right flat.

---

## So How *Do* We Make a Local Server Public?

If you ever *do* want to expose your server to the internet (carefully), you can:

* Use tools like [Ngrok](https://ngrok.com/) or [Localtunnel](https://theboroer.github.io/localtunnel-www/) to safely expose your local server temporarily.
* Configure **port forwarding** on your Wi-Fi router (only if you *really* know what you’re doing—hello, security risks!).

But for now, just remember:

> A local IP is like your nickname at home—only your housemates know it. A public IP is your mailing address—visible to the world, but protected by doors and locks (aka NAT & firewalls).

---

## Want to Dig Deeper?

* [Private vs Public IP (Cloudflare)](https://www.cloudflare.com/learning/network-layer/what-is-an-ip-address/)
* [Python HTTP Server Basics (RealPython)](https://realpython.com/python-http-server/)

---
